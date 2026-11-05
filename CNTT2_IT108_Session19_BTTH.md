# BÀI TỔNG HỢP: RÀ SOÁT AN TOÀN THÔNG TIN TRƯỚC KHI BÀN GIAO DỰ ÁN SMARTCAMPUS

## PHẦN 1 – NHẬN DIỆN RỦI RO VÀ XỬ LÝ SỰ CỐ

### 1. Tình huống 1 – Email giả mạo GitHub

Đây là hình thức **Phishing (lừa đảo qua email)**. Email tạo cảm giác tài khoản GitHub bị khóa để người nhận lo lắng và bấm vào đường dẫn.

Dấu hiệu đáng ngờ là:
- Đường dẫn `github-security.com` không phải tên miền chính thức `github.com`.
- Email yêu cầu nhập lại mật khẩu để mở khóa tài khoản.
- Tiêu đề cảnh báo tài khoản bị khóa dễ khiến người nhận vội vàng làm theo.

Vì vậy, không bấm liên kết trong email và không nhập mật khẩu. Nên tự mở GitHub bằng địa chỉ quen thuộc để kiểm tra thông báo.

### 2. Tình huống 2 – Trang web chia sẻ phần mềm crack

Đây là **bẫy phát tán mã độc qua phần mềm crack**, có sử dụng kỹ thuật Social Engineering để dụ người dùng tự tắt công cụ bảo vệ. Mã độc có thể được ngụy trang trong tệp cài đặt.

Yêu cầu tắt Windows Defender rất nguy hiểm vì nó làm giảm khả năng phát hiện và ngăn chặn tệp độc hại. Nếu tiếp tục chạy tệp, máy có thể bị cài mã độc, đánh cắp mật khẩu, dữ liệu hoặc thông tin đăng nhập. Ảnh đề bài không cung cấp tên miền của trang web nên chưa đủ căn cứ để kết luận đây là Typosquatting.

### 3. Đối chiếu với Quy tắc 5 KHÔNG

- **Tình huống 1:** Không bấm vào liên kết đáng ngờ và không cung cấp mật khẩu hoặc mã OTP qua email/link lạ.
- **Tình huống 2:** Không tải, cài hoặc chạy phần mềm crack từ nguồn không rõ ràng; tuyệt đối không tắt phần mềm bảo vệ theo yêu cầu của trang web.

### 4. Bốn bước cấp cứu nếu đã tải và chạy file crack

1. **Ngắt kết nối mạng:** Tắt Wi-Fi hoặc rút dây mạng để hạn chế mã độc liên lạc ra ngoài hoặc tiếp tục gửi dữ liệu.
2. **Báo người phụ trách:** Báo ngay cho trưởng nhóm hoặc bộ phận IT; không tiếp tục đăng nhập tài khoản trên máy nghi nhiễm.
3. **Cách ly và kiểm tra máy:** Nhờ người có chuyên môn quét, xử lý mã độc và cài lại hệ thống từ nguồn sạch nếu cần. Không tự ý chép dữ liệu nghi nhiễm sang máy khác.
4. **Bảo vệ lại tài khoản:** Dùng một thiết bị sạch để đổi mật khẩu, đăng xuất các phiên lạ, thu hồi token/khóa truy cập có nguy cơ bị lộ và kiểm tra lại 2FA.

## PHẦN 2 – CHUYỂN SANG PASSWORD MANAGER

### 1. Rủi ro khi dùng chung một mật khẩu

Nếu mật khẩu email nhóm bị lộ, kẻ tấn công có thể thử chính cặp thông tin đăng nhập đó trên GitHub và Vercel. Đây là **Credential Stuffing** khi kẻ tấn công tự động thử thông tin đăng nhập đã bị lộ trên các dịch vụ khác. Hậu quả có thể là chiếm quyền tài khoản và làm lộ mã nguồn hoặc quyền triển khai dự án.

### 2. Vì sao Zero-Knowledge Architecture an toàn hơn?

Với kiến trúc Zero-Knowledge, dữ liệu trong két mật khẩu được mã hóa ngay trên thiết bị người dùng trước khi gửi lên máy chủ. Máy chủ chủ yếu lưu dữ liệu đã mã hóa, không giữ khóa cần thiết để tự giải mã nội dung két. Vì vậy, nếu máy chủ bị xâm nhập, kẻ tấn công không thể đọc ngay mật khẩu bên trong. Tuy nhiên, người dùng vẫn cần Master Password mạnh, 2FA và thiết bị sạch vì mật khẩu yếu hoặc máy cá nhân bị nhiễm mã độc vẫn có thể gây rò rỉ.

### 3. Cấu hình Password Generator

Dùng cùng một cấu hình an toàn nhưng tạo **ba mật khẩu ngẫu nhiên khác nhau**, không tự đặt theo tên dự án hoặc ngày tháng.

| Thông số | GitHub | Vercel | Email nhóm |
|---|---:|---:|---:|
| Độ dài | 24 ký tự | 24 ký tự | 24 ký tự |
| Chữ hoa (A-Z) | Có | Có | Có |
| Chữ thường (a-z) | Có | Có | Có |
| Chữ số (0-9) | Có | Có | Có |
| Ký tự đặc biệt | Có | Có | Có |

Sau khi tạo, lưu từng mật khẩu vào mục đăng nhập riêng trong Password Manager. Không dùng lại cùng một mật khẩu giữa các dịch vụ.

## PHẦN 3 – KÍCH HOẠT 2FA CHO TÀI KHOẢN GITHUB TỔ CHỨC

### 1. Vì sao nên chọn Authenticator App (TOTP) thay SMS OTP?

SMS OTP có hai nhược điểm chính:
- Có nguy cơ bị chiếm quyền số điện thoại qua SIM Swapping hoặc khai thác lỗ hổng mạng di động.
- Phụ thuộc vào sóng điện thoại và khả năng nhận tin nhắn, nên có thể bất tiện khi ở nước ngoài hoặc mất sóng.

Authenticator App tạo mã TOTP ngay trên thiết bị, không cần mạng di động để sinh mã. GitHub cũng khuyến nghị dùng ứng dụng TOTP thay SMS. Nếu hai người thực sự được phép dùng chung một tài khoản, có thể quét mã QR trên cả hai thiết bị ngay trong lúc thiết lập, nhưng cách tốt hơn vẫn là mỗi người có tài khoản riêng và bật 2FA riêng để dễ quản lý trách nhiệm.

### 2. Các bước bật 2FA bằng Google Authenticator

1. Cài Google Authenticator trên điện thoại.
2. Đăng nhập GitHub, mở **Settings** → **Password and authentication**.
3. Trong phần **Two-factor authentication**, chọn bật 2FA và chọn ứng dụng Authenticator.
4. Dùng Google Authenticator quét mã QR. Nếu có hai thiết bị được phép cùng dùng một tài khoản, quét mã trên cả hai thiết bị trong cùng lúc thiết lập; không gửi ảnh QR hoặc khóa thiết lập cho người khác.
5. Nhập mã gồm 6 chữ số đang hiển thị trong ứng dụng để xác nhận.
6. Tải và lưu các mã khôi phục ở nơi an toàn trước khi hoàn tất.

### 3. Lưu trữ mã khôi phục

Mã khôi phục giúp đăng nhập lại khi mất điện thoại hoặc không dùng được ứng dụng Authenticator. Mỗi mã chỉ nên dùng một lần.

Hai nơi nên lưu:
- Một bản in giấy, cất trong két hoặc ngăn tủ có khóa và chỉ người có trách nhiệm được quyền truy cập.
- Một bản sao được bảo vệ trong kho lưu trữ mã hóa, tách biệt với điện thoại đang dùng Authenticator.

Không nên chụp ảnh màn hình rồi để trong thư viện ảnh, gửi qua email/nhóm chat hoặc lưu tệp không mã hóa trên cùng điện thoại. Không chia sẻ mã khôi phục công khai.

## PHẦN 4 – BẢO VỆ SECRETS TRƯỚC KHI PUSH CODE

### 1. Hai giá trị Secret đang bị hardcode

- `API_KEY`: khóa API của dịch vụ.
- `DB_PASSWORD`: mật khẩu cơ sở dữ liệu.

Hai giá trị này không được viết trực tiếp trong mã nguồn hoặc đẩy lên GitHub công khai. Nếu là khóa/mật khẩu thật đã từng được đưa lên kho mã nguồn, cần thu hồi hoặc đổi ngay.

### 2. Đoạn code sau khi sửa

```js
require("dotenv").config();

const API_KEY = process.env.API_KEY;
const DB_PASSWORD = process.env.DB_PASSWORD;

if (!API_KEY || !DB_PASSWORD) {
  throw new Error("Thiếu API_KEY hoặc DB_PASSWORD trong file .env");
}

function connectToDatabase() {
  return connect(DB_PASSWORD);
}

// Dùng API_KEY tại nơi gọi dịch vụ cần xác thực.
```

Cài thư viện đọc biến môi trường nếu dự án chưa có:

```bash
npm install dotenv
```

### 3. Nội dung ba file cần có

**File `.env`** – chỉ lưu trên máy cá nhân hoặc môi trường triển khai an toàn. Do đề bài không cung cấp khóa API và mật khẩu cơ sở dữ liệu thật, hai dòng dưới đây là chỗ giữ chỗ; cần thay bằng giá trị thật tại máy cá nhân, không đưa giá trị thật vào báo cáo hoặc GitHub.

```env
API_KEY=THAY_BANG_API_KEY_THAT
DB_PASSWORD=THAY_BANG_MAT_KHAU_CSDL_RIENG
```

**File `.gitignore`** – ngăn Git đưa file chứa bí mật lên kho mã nguồn:

```gitignore
node_modules/
.env
.env.*
!.env.example
```

**File `.env.example`** – chỉ chia sẻ tên biến, không chứa giá trị thật:

```env
API_KEY=
DB_PASSWORD=
```

### 4. Kiểm tra trước khi push

1. Tìm trong mã nguồn xem còn API key, mật khẩu, token hoặc chuỗi bí mật nào đang viết trực tiếp hay không.
2. Kiểm tra `.env` đã nằm trong `.gitignore`; bảo đảm `.env.example` chỉ có tên biến và không có giá trị thật.
3. Xem kỹ `git status` và `git diff --cached` để chắc chắn không đưa `.env`, tệp cấu hình riêng hoặc dữ liệu nhạy cảm vào vùng chuẩn bị commit.
4. Kiểm tra lại nội dung commit và quyền truy cập repository trước khi push. Nếu phát hiện Secret từng bị đẩy lên Git, phải thu hồi/đổi Secret; chỉ xóa dòng đó ở commit mới là chưa đủ.

## KẾT LUẬN

Nhóm nên dùng mật khẩu riêng cho từng dịch vụ, quản lý bằng Password Manager, bật 2FA bằng ứng dụng Authenticator và không lưu Secret trực tiếp trong mã nguồn. Trước khi bàn giao SmartCampus, cần rà soát email đáng ngờ, thiết bị có nguy cơ nhiễm mã độc và toàn bộ nội dung chuẩn bị đưa lên GitHub để hạn chế rò rỉ tài khoản, dữ liệu và mã nguồn.

