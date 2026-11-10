# BeKyredezcutiii🦖

Website bán hàng chạy bằng Node.js + PostgreSQL. Một dịch vụ duy nhất phục vụ cả giao diện và API.

## Triển khai (Render, Railway hoặc VPS)
1. Tạo database PostgreSQL (Supabase, Neon hoặc Render) và lấy `DATABASE_URL`.
2. Đẩy mã nguồn lên GitHub, tạo Web Service Node.js: build `npm install`, start `npm start`.
3. Đặt biến môi trường theo `.env.example`:
   - `JWT_SECRET`: chuỗi ngẫu nhiên dài
   - `ADMIN_USER`: tên đăng nhập admin, chỉ chữ, số, gạch dưới (ví dụ `bekyredezcutiii`)
   - `ADMIN_DISPLAY`: `BeKyredezcutiii🦖`
   - `ADMIN_PASSWORD`: mật khẩu admin
   - `WEBHOOK_SECRET`: khóa cho webhook ngân hàng
   - `NODE_ENV=production`
4. Lần chạy đầu server tự tạo bảng và tài khoản Admin.
5. Đăng nhập Admin, vào Quản trị để thiết lập ngân hàng, QR, banner, danh mục và sản phẩm.

## Nạp tiền tự động
Dịch vụ như SePay hoặc Casso gửi webhook tới `POST /api/webhook/bank` với header `x-webhook-secret` và body JSON `{"txid":"...","amount":100000,"content":"VN1 tentaikhoan"}`. Mỗi `txid` chỉ được cộng một lần. Bạn cần map trường của nhà cung cấp sang 3 trường trên. Không có webhook thì Admin xác nhận thủ công ở tab Giao dịch.

## Chạy thử trên máy
```
npm install
DATABASE_URL=... JWT_SECRET=... ADMIN_USER=admin ADMIN_PASSWORD=... npm start
```

## Chưa có trong bản này
Tải ảnh lên (hiện dán đường dẫn https), sắp xếp kéo thả, tạo Admin thứ hai, AI Admin Assistant, trang chỉnh bố cục trực tiếp.

## Nếu đặt giao diện trên Netlify
Sửa `DOI-THANH-DOMAIN-BACKEND` trong `netlify.toml` thành domain backend, publish thư mục `public`. Đăng nhập Admin bằng `ADMIN_USER` hoặc tên hiển thị `BeKyredezcutiii🦖`.
