# Hướng Dẫn Sử Dụng Source Trang Workshop `/laodong`

## 1. Mở file nào để sửa?

File cần sửa gần như toàn bộ nội dung là:

```text
suc_ben_hud/lao_dong/index.html
```

Bạn có thể mở file này bằng VS Code, Notepad++, Cursor, Antigravity, hoặc bất kỳ trình sửa code/text nào.

Không nên sửa các file khác nếu bạn không chắc chúng dùng để làm gì.

## 2. Những nơi cần đổi trước khi đăng web

Trong `suc_ben_hud/lao_dong/index.html`, hãy tìm và đổi các nội dung sau:

- Tên workshop.
- Ngày giờ tổ chức.
- Địa điểm.
- Tên đơn vị/thương hiệu.
- Nội dung giới thiệu.
- Link nút đăng ký.
- Hình ảnh, nếu muốn thay.

Link đăng ký hiện đang là link mẫu:

```text
https://forms.gle/your-registration-form
```

Hãy thay link này bằng Google Form thật của bạn.

Trong file có 2 nút đăng ký, nên hãy tìm `forms.gle` và thay tất cả kết quả tìm thấy.

## 3. Đổi hình ảnh như thế nào?

Hình ảnh nằm trong thư mục:

```text
suc_ben_hud/lao_dong
```

Nếu muốn thay ảnh, cách dễ nhất là:

- Chuẩn bị ảnh mới cùng định dạng `.png`.
- Đổi tên ảnh mới giống tên ảnh cũ.
- Copy ảnh mới vào thư mục `suc_ben_hud/lao_dong`.
- Chấp nhận ghi đè ảnh cũ.

Cách này giúp bạn không cần sửa code đường dẫn ảnh.

## 4. Xem thử trên máy

Cách xem đúng nhất là nhờ người biết máy tính chạy lệnh bên dưới trong PowerShell, tại thư mục source này:

```powershell
npx firebase-tools emulators:start --only hosting --project demo-laodong
```

Sau đó mở:

```text
http://127.0.0.1:5000/laodong
```

Nếu chỉ muốn xem nhanh, có thể chạy:

```powershell
npx serve suc_ben_hud
```

Sau đó mở:

```text
http://localhost:3000/lao_dong/
```

Lưu ý: không nên double-click trực tiếp vào file `index.html`, vì hình ảnh có thể không hiển thị đúng.

## 5. Đưa web lên mạng bằng Firebase

Người deploy cần có:

- Tài khoản Google/Firebase riêng.
- Firebase project riêng.
- Node.js đã cài trên máy.

Chạy các lệnh sau trong PowerShell, tại thư mục source:

```powershell
npx firebase-tools login
npx firebase-tools deploy --project YOUR_FIREBASE_PROJECT_ID
```

Thay `YOUR_FIREBASE_PROJECT_ID` bằng project ID Firebase của bạn.

Sau khi deploy thành công, Firebase sẽ hiện link web. Trang sẽ mở được theo dạng:

```text
https://TEN_PROJECT.web.app/laodong
```

## 6. Khi sửa xong nên đổi version

Bước này giúp người xem cũ nhận bản mới, tránh bị lưu cache.

Mở file:

```text
suc_ben_hud/version.json
```

Đổi:

```text
laodong-workshop-v1
```

thành:

```text
laodong-workshop-v2
```

Sau đó mở file:

```text
suc_ben_hud/lao_dong/index.html
```

Tìm dòng:

```js
const CURRENT_VERSION = "laodong-workshop-v1";
```

Đổi thành:

```js
const CURRENT_VERSION = "laodong-workshop-v2";
```

Nếu sau này sửa nữa, đổi tiếp thành `v3`, `v4`, ...

## 7. Kiểm tra trước khi gửi link cho khách

Hãy mở web trên điện thoại và máy tính, rồi kiểm tra:

- Trang `/laodong` mở đúng.
- Nút đăng ký mở đúng Google Form của bạn.
- Ngày giờ đã đúng.
- Địa điểm đã đúng.
- Hình ảnh hiển thị đầy đủ.
- Không còn thông tin cũ của người gửi source.
