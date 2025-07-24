# BUỔI 3: CSS (PHẦN 2)

## 🧩 Phần 1: Flex và Grid Layout

Flexbox và CSS Grid là hai "linh hồn" của bố cục web hiện đại, cho phép các nhà phát triển tạo ra các giao diện phức tạp và đáp ứng một cách hiệu quả hơn bao giờ hết. Chúng ta sẽ khám phá chi tiết hơn về cách thức hoạt động và các khả năng của từng module.

### 🔸 1.1 Flexbox

**Flexbox (Flexible Box Layout)** được thiết kế để phân phối và căn chỉnh các phần tử trong một container dọc theo một chiều duy nhất (một hàng hoặc một cột). Đây là công cụ hoàn hảo cho các thành phần UI cần sắp xếp theo một trục, ví dụ như thanh điều hướng, danh sách sản phẩm, hoặc các nhóm nút.

---

#### Khái niệm cốt lõi:

- **Flex Container**: Phần tử cha mà bạn áp dụng `display: flex;`. Nó trở thành môi trường để sắp xếp các phần tử con.
- **Flex Item**: Các phần tử con trực tiếp của Flex Container. Chúng sẽ được sắp xếp theo quy tắc của Flexbox.
- **Main Axis (Trục Chính)**: Trục mà các flex item được sắp xếp theo. Hướng của trục này được xác định bởi `flex-direction`.
- **Cross Axis (Trục Phụ)**: Trục vuông góc với trục chính.

---

#### Các thuộc tính trên **Flex Container**:

| Thuộc tính        | Giá trị phổ biến và Ý nghĩa                                                                                                                                                                                                                                                                                                                                                                                                                  |
| :---------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `display`         | - `flex`: Biến phần tử thành **flex container** dạng block-level.\<br\>- `inline-flex`: Biến phần tử thành **flex container** dạng inline-level.                                                                                                                                                                                                                                                                                             |
| `flex-direction`  | - `row` (mặc định): Trục chính theo chiều ngang, từ trái sang phải.\<br\>- `column`: Trục chính theo chiều dọc, từ trên xuống dưới.\<br\>- `row-reverse`: Trục chính theo chiều ngang, từ phải sang trái.\<br\>- `column-reverse`: Trục chính theo chiều dọc, từ dưới lên trên.                                                                                                                                                              |
| `flex-wrap`       | - `nowrap` (mặc định): Các item cố gắng nằm trên một dòng duy nhất, có thể bị tràn.\<br\>- `wrap`: Các item tự động xuống dòng khi không đủ không gian.\<br\>- `wrap-reverse`: Các item xuống dòng theo chiều ngược lại.                                                                                                                                                                                                                     |
| `flex-flow`       | Là thuộc tính viết tắt cho `flex-direction` và `flex-wrap`. Ví dụ: `flex-flow: row wrap;`                                                                                                                                                                                                                                                                                                                                                    |
| `justify-content` | Căn chỉnh các flex item dọc theo **trục chính** của container.\<br\>- `flex-start` (mặc định): Căn lề đầu trục.\<br\>- `flex-end`: Căn lề cuối trục.\<br\>- `center`: Căn giữa.\<br\>- `space-between`: Phân phối đều không gian giữa các item, item đầu tiên ở đầu, item cuối cùng ở cuối.\<br\>- `space-around`: Phân phối đều không gian xung quanh mỗi item.\<br\>- `space-evenly`: Phân phối đều không gian giữa các item và ở hai đầu. |
| `align-items`     | Căn chỉnh các flex item dọc theo **trục phụ** của container.\<br\>- `stretch` (mặc định): Các item kéo dài để lấp đầy container.\<br\>- `flex-start`: Căn lề đầu trục phụ.\<br\>- `flex-end`: Căn lề cuối trục phụ.\<br\>- `center`: Căn giữa.\<br\>- `baseline`: Căn chỉnh dựa trên đường cơ sở của nội dung.                                                                                                                               |
| `align-content`   | Căn chỉnh các **nhóm dòng** dọc theo trục phụ khi có nhiều dòng (chỉ có tác dụng khi `flex-wrap` là `wrap`). Các giá trị tương tự `justify-content`. Khi chỉ có một dòng, thuộc tính này không có tác dụng.                                                                                                                                                                                                                                  |
| `gap`             | Tạo khoảng cách giữa các flex item. Là viết tắt của `row-gap` và `column-gap`. Ví dụ: `gap: 10px;` (cả hàng và cột) hoặc `gap: 10px 20px;` (hàng 10px, cột 20px).                                                                                                                                                                                                                                                                            |

---

#### Các thuộc tính trên **Flex Item**:

| Thuộc tính    | Giá trị và Ý nghĩa                                                                                                                                                           |
| :------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `order`       | Mặc định là `0`. Cho phép thay đổi thứ tự hiển thị của các item độc lập với thứ tự trong HTML. Giá trị số nguyên (âm, 0, dương). Item có `order` nhỏ hơn sẽ xuất hiện trước. |
| `flex-grow`   | Mặc định là `0`. Xác định khả năng của item để "phát triển" (tăng kích thước) để lấp đầy không gian trống trong container. Giá trị số không âm.                              |
| `flex-shrink` | Mặc định là `1`. Xác định khả năng của item để "co lại" (giảm kích thước) khi không gian không đủ. Giá trị số không âm.                                                      |
| `flex-basis`  | Mặc định là `auto`. Xác định kích thước mặc định của item trước khi không gian được phân phối. Có thể dùng đơn vị như `px`, `%`, `em`, v.v. hoặc `auto`.                     |
| `flex`        | Là thuộc tính viết tắt cho `flex-grow`, `flex-shrink`, và `flex-basis`. Ví dụ: `flex: 1 1 auto;` (tương đương `flex: auto;`) hoặc `flex: 1;` (tương đương `flex: 1 1 0%;`).  |
| `align-self`  | Ghi đè thuộc tính `align-items` của container cho một item cụ thể. Các giá trị tương tự `align-items`.                                                                       |

---

### 🔸 1.2 Grid Layout

**CSS Grid Layout** là một hệ thống lưới hai chiều (hàng và cột), lý tưởng để tạo các bố cục trang tổng thể phức tạp hơn. Nó cho phép bạn xác định một cấu trúc lưới rõ ràng và sau đó đặt các phần tử vào các ô hoặc khu vực cụ thể trong lưới đó.

---

#### Khái niệm cốt lõi:

- **Grid Container**: Phần tử cha mà bạn áp dụng `display: grid;` hoặc `display: inline-grid;`.
- **Grid Item**: Các phần tử con trực tiếp của Grid Container.
- **Grid Lines (Đường lưới)**: Các đường ngang và dọc phân chia lưới. Chúng được đánh số từ 1.
- **Grid Tracks (Vết lưới)**: Không gian giữa hai đường lưới liên tiếp (là các hàng hoặc cột).
- **Grid Cells (Ô lưới)**: Không gian được tạo bởi sự giao nhau của một hàng và một cột.
- **Grid Areas (Khu vực lưới)**: Một khu vực hình chữ nhật được tạo thành từ một hoặc nhiều ô lưới.

---

#### Các thuộc tính trên **Grid Container**:

| Thuộc tính              | Giá trị và Ý nghĩa                                                                                                                                                                                                                                                                                                                                                |
| :---------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `display`               | - `grid`: Biến phần tử thành **grid container** dạng block-level.\<br\>- `inline-grid`: Biến phần tử thành **grid container** dạng inline-level.                                                                                                                                                                                                                  |
| `grid-template-columns` | Xác định số lượng và kích thước của các **cột**. Có thể dùng các giá trị cụ thể (`px`, `%`, `em`), đơn vị linh hoạt `fr` (fractional unit - phân chia không gian còn lại), hoặc các hàm như `repeat()`, `minmax()`, `auto-fill`, `auto-fit`.\<br\>Ví dụ: `grid-template-columns: 100px 1fr 2fr;` hoặc `grid-template-columns: repeat(3, 1fr);` (3 cột bằng nhau). |
| `grid-template-rows`    | Xác định số lượng và kích thước của các **hàng**. Tương tự `grid-template-columns`, thường dùng `auto` để hàng tự động điều chỉnh kích thước theo nội dung.\<br\>Ví dụ: `grid-template-rows: auto 200px 1fr;`                                                                                                                                                     |
| `grid-template-areas`   | Định nghĩa các khu vực được đặt tên trong lưới bằng cách sử dụng các chuỗi ký tự. Các khu vực phải tạo thành hình chữ nhật. `.` biểu thị ô trống.\<br\>Ví dụ:\<br\>`"header header header"`\<br\>`"nav main aside"`\<br\>`"footer footer footer"`                                                                                                                 |
| `gap`                   | Viết tắt của `row-gap` và `column-gap`. Tạo khoảng cách giữa các hàng và cột.\<br\>Ví dụ: `gap: 15px;` (hàng và cột đều 15px) hoặc `gap: 10px 20px;` (row-gap 10px, column-gap 20px).                                                                                                                                                                             |
| `row-gap`               | Khoảng cách giữa các hàng.                                                                                                                                                                                                                                                                                                                                        |
| `column-gap`            | Khoảng cách giữa các cột.                                                                                                                                                                                                                                                                                                                                         |
| `justify-items`         | Căn chỉnh nội dung của các grid item dọc theo **trục nội tuyến** (inline axis - thường là chiều ngang) bên trong ô lưới của chúng.\<br\>- `start`, `end`, `center`, `stretch` (mặc định).                                                                                                                                                                         |
| `align-items`           | Căn chỉnh nội dung của các grid item dọc theo **trục khối** (block axis - thường là chiều dọc) bên trong ô lưới của chúng.\<br\>- `start`, `end`, `center`, `stretch` (mặc định).                                                                                                                                                                                 |
| `place-items`           | Viết tắt của `align-items` và `justify-items`. Ví dụ: `place-items: center;` hoặc `place-items: start end;`.                                                                                                                                                                                                                                                      |
| `justify-content`       | Căn chỉnh **toàn bộ lưới** dọc theo trục nội tuyến khi tổng kích thước của các cột nhỏ hơn kích thước container.\<br\>- `start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`.                                                                                                                                                                |
| `align-content`         | Căn chỉnh **toàn bộ lưới** dọc theo trục khối khi tổng kích thước của các hàng nhỏ hơn kích thước container.\<br\>- `start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`.                                                                                                                                                                    |
| `place-content`         | Viết tắt của `align-content` và `justify-content`. Ví dụ: `place-content: center;` hoặc `place-content: start end;`.                                                                                                                                                                                                                                              |
| `grid-auto-columns`     | Xác định kích thước cho các cột được tạo tự động (implicit tracks) khi có nhiều item hơn số cột được định nghĩa.                                                                                                                                                                                                                                                  |
| `grid-auto-rows`        | Xác định kích thước cho các hàng được tạo tự động (implicit tracks) khi có nhiều item hơn số hàng được định nghĩa.                                                                                                                                                                                                                                                |
| `grid-auto-flow`        | Kiểm soát cách các item không được đặt rõ ràng được đặt vào lưới: `row` (mặc định), `column`, `row dense`, `column dense`.                                                                                                                                                                                                                                        |

---

#### Các thuộc tính trên **Grid Item**:

| Thuộc tính          | Giá trị và Ý nghĩa                                                                                                                                                                                           |
| :------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `grid-column-start` | Xác định đường lưới bắt đầu của item theo chiều ngang. Có thể là số dòng, tên dòng, hoặc `span` số lượng cột.                                                                                                |
| `grid-column-end`   | Xác định đường lưới kết thúc của item theo chiều ngang. Tương tự `grid-column-start`.                                                                                                                        |
| `grid-row-start`    | Xác định đường lưới bắt đầu của item theo chiều dọc. Tương tự `grid-column-start`.                                                                                                                           |
| `grid-row-end`      | Xác định đường lưới kết thúc của item theo chiều dọc. Tương tự `grid-column-end`.                                                                                                                            |
| `grid-column`       | Viết tắt của `grid-column-start` và `grid-column-end`. Ví dụ: `grid-column: 1 / 3;` (từ dòng 1 đến dòng 3) hoặc `grid-column: span 2;` (kéo dài 2 cột).                                                      |
| `grid-row`          | Viết tắt của `grid-row-start` và `grid-row-end`. Ví dụ: `grid-row: 2 / span 2;` (từ dòng 2 kéo dài 2 hàng).                                                                                                  |
| `grid-area`         | - Gán một item cho một khu vực đã đặt tên trong `grid-template-areas`.\<br\>- Hoặc là viết tắt cho `grid-row-start / grid-column-start / grid-row-end / grid-column-end`. Ví dụ: `grid-area: 1 / 2 / 3 / 4;` |
| `justify-self`      | Ghi đè `justify-items` của container cho một item cụ thể, căn chỉnh item dọc theo trục nội tuyến trong ô của nó.\<br\>- `start`, `end`, `center`, `stretch` (mặc định).                                      |
| `align-self`        | Ghi đè `align-items` của container cho một item cụ thể, căn chỉnh item dọc theo trục khối trong ô của nó.\<br\>- `start`, `end`, `center`, `stretch` (mặc định).                                             |
| `place-self`        | Viết tắt của `align-self` và `justify-self`. Ví dụ: `place-self: center;` hoặc `place-self: start end;`.                                                                                                     |

---

## 📱 Phần 2: Responsive Design

**Responsive Design (Thiết kế đáp ứng)** là triết lý thiết kế và phát triển web cho phép trang web thay đổi bố cục và/hoặc hành vi của nó dựa trên kích thước màn hình, nền tảng và hướng của thiết bị. Mục tiêu là cung cấp trải nghiệm xem và tương tác tối ưu cho người dùng trên mọi thiết bị.

### 🔸 2.1 Media Queries

**Media Queries** là cốt lõi của Responsive Design. Chúng cho phép bạn áp dụng các kiểu CSS khác nhau dựa trên các "điều kiện" của thiết bị truy cập trang web.

---

#### Cú pháp và đặc điểm chính:

| Cú pháp/Đặc điểm                                            | Ý nghĩa và Cách sử dụng                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| :---------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `@media media-type and (media-feature) { /* CSS rules */ }` | **Cấu trúc cơ bản**: Bắt đầu bằng `@media`, theo sau là kiểu phương tiện (media type) và một hoặc nhiều điều kiện (media features). Các quy tắc CSS bên trong chỉ được áp dụng nếu điều kiện đúng.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **`media-type`**                                            | - `all`: Cho tất cả các loại thiết bị.\<br\>- `screen`: Dành cho màn hình máy tính, điện thoại, máy tính bảng.\<br\>- `print`: Dành cho trang in.\<br\>- `speech`: Dành cho các thiết bị đọc màn hình.\<br\>(Thường dùng `screen` hoặc bỏ qua `media-type` để mặc định là `all` nếu chỉ có `media-feature`).                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **`media-feature`**                                         | Các điều kiện phổ biến:\<br\>- `max-width`: Áp dụng khi chiều rộng khung nhìn (viewport) **tối đa** là giá trị này. Rất phổ biến trong chiến lược **desktop-first** (thiết kế cho desktop trước, sau đó co lại cho mobile).\<br\>- `min-width`: Áp dụng khi chiều rộng khung nhìn (viewport) **tối thiểu** là giá trị này. Rất phổ biến trong chiến lược **mobile-first** (thiết kế cho mobile trước, sau đó mở rộng cho desktop).\<br\>- `orientation`: `portrait` (dọc) hoặc `landscape` (ngang).\<br\>- `min-height`, `max-height`: Chiều cao khung nhìn.\<br\>- `min-resolution`, `max-resolution`: Độ phân giải màn hình.\<br\>- `aspect-ratio`: Tỷ lệ khung hình của khung nhìn.\<br\>- `prefers-color-scheme`: `light` hoặc `dark` (chế độ sáng/tối). |
| **Toán tử logic**                                           | - `and`: Kết hợp nhiều điều kiện (tất cả phải đúng). Ví dụ: `@media screen and (min-width: 768px) and (max-width: 1024px) { ... }`\<br\>- `,` (or): Áp dụng nếu ít nhất một điều kiện đúng. Ví dụ: `@media screen and (max-width: 600px), print { ... }`\<br\>- `not`: Phủ định một điều kiện. Ví dụ: `@media not screen and (min-width: 1200px) { ... }`                                                                                                                                                                                                                                                                                                                                                                                                    |
| **`meta name="viewport"`**                                  | Đây là thẻ meta **cực kỳ quan trọng** được đặt trong phần `<head>` của HTML:\<br\>`<meta name="viewport" content="width=device-width, initial-scale=1.0">`\<br\>- `width=device-width`: Đặt chiều rộng của khung nhìn bằng chiều rộng của thiết bị (trong các pixel độc lập với thiết bị).\<br\>- `initial-scale=1.0`: Đặt mức phóng đại ban đầu khi trang web được tải. Nếu không có dòng này, thiết bị di động có thể render trang web ở kích thước desktop rồi phóng nhỏ lại, làm hỏng bố cục responsive.                                                                                                                                                                                                                                                 |
| **Breakpoints**                                             | Các điểm chiều rộng màn hình cụ thể (ví dụ: 576px, 768px, 992px, 1200px) nơi bạn thay đổi bố cục trang web bằng Media Queries. Việc lựa chọn breakpoints phụ thuộc vào nội dung và thiết kế của bạn.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

---

#### Chiến lược Responsive Design:

1.  **Mobile-First (Ưu tiên di động)**:

    - Bắt đầu bằng cách thiết kế và phát triển cho màn hình nhỏ nhất (di động) trước.
    - CSS mặc định được viết cho thiết bị di động.
    - Sử dụng `min-width` trong Media Queries để thêm các kiểu dáng cho màn hình lớn hơn.
    - **Ưu điểm**: Đảm bảo hiệu suất tốt trên di động, tập trung vào nội dung thiết yếu, dễ mở rộng lên màn hình lớn hơn.
    - **Ví dụ**:

      ```css
      /* CSS mặc định cho di động */
      body {
        font-size: 16px;
      }
      .container {
        grid-template-columns: 1fr;
      }

      @media (min-width: 768px) {
        /* CSS cho máy tính bảng trở lên */
        .container {
          grid-template-columns: repeat(2, 1fr);
        }
      }

      @media (min-width: 1024px) {
        /* CSS cho desktop trở lên */
        .container {
          grid-template-columns: repeat(3, 1fr);
        }
      }
      ```

2.  **Desktop-First (Ưu tiên máy tính để bàn)**:

    - Bắt đầu bằng cách thiết kế và phát triển cho màn hình lớn (desktop) trước.
    - CSS mặc định được viết cho thiết bị desktop.
    - Sử dụng `max-width` trong Media Queries để điều chỉnh kiểu dáng cho màn hình nhỏ hơn.
    - **Ưu điểm**: Phù hợp với các dự án ban đầu được thiết kế cho desktop, dễ dàng thu nhỏ.
    - **Ví dụ**:

      ```css
      /* CSS mặc định cho desktop */
      body {
        font-size: 18px;
      }
      .container {
        grid-template-columns: repeat(3, 1fr);
      }

      @media (max-width: 1024px) {
        /* CSS cho máy tính bảng trở xuống */
        .container {
          grid-template-columns: repeat(2, 1fr);
        }
      }

      @media (max-width: 768px) {
        /* CSS cho di động trở xuống */
        .container {
          grid-template-columns: 1fr;
        }
      }
      ```

---

## 🎨 Phần 3: Style một số thành phần cơ bản

Việc tạo kiểu cho các thành phần UI cơ bản không chỉ làm cho trang web trông chuyên nghiệp hơn mà còn cải thiện đáng kể **Trải nghiệm người dùng (UX)**. Dưới đây là các kỹ thuật và thuộc tính chi tiết hơn để tùy chỉnh các thành phần phổ biến.

### 🔸 3.1 Dropdown (`<select>`)

Thành phần `<select>` là một hộp chọn cho phép người dùng lựa chọn một hoặc nhiều tùy chọn từ danh sách. Mặc dù trình duyệt cung cấp kiểu dáng mặc định, chúng thường không đẹp mắt và không đồng nhất giữa các trình duyệt. Do đó, việc tùy chỉnh là cần thiết.

---

#### Các thuộc tính CSS thường dùng cho `<select>`:

| Thuộc tính                                                    | Ý nghĩa và Cách sử dụng                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :------------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `padding`                                                     | Tăng khoảng cách giữa nội dung và viền của select, làm cho nó dễ bấm hơn và có vẻ ngoài lớn hơn.                                                                                                                                                                                                                                                                                                                                                           |
| `border`, `border-radius`                                     | Định kiểu viền và bo tròn các góc. `border: 1px solid #ccc;` và `border-radius: 5px;` là các giá trị phổ biến.                                                                                                                                                                                                                                                                                                                                             |
| `background-color`                                            | Đặt màu nền cho select.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `font-size`, `color`                                          | Tùy chỉnh kích thước và màu chữ bên trong select.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `appearance: none;`                                           | **Cực kỳ quan trọng\!** Loại bỏ hoàn toàn giao diện mặc định của dropdown do trình duyệt cung cấp. Để đảm bảo tương thích đa trình duyệt, nên dùng các tiền tố nhà cung cấp:\<br\>- `appearance: none;`\<br\>- `-webkit-appearance: none;` (cho Chrome, Safari, Edge)\<br\>- `-moz-appearance: none;` (cho Firefox)\<br\>Khi sử dụng thuộc tính này, mũi tên dropdown mặc định sẽ biến mất, cho phép bạn thay thế bằng hình ảnh hoặc biểu tượng tùy chỉnh. |
| `background-image`                                            | Sau khi ẩn `appearance`, bạn có thể thêm một mũi tên tùy chỉnh bằng cách sử dụng `background-image`. Có thể dùng hình ảnh `.png`, `.svg` hoặc **SVG inline data URI** (như trong ví dụ trước để tránh request HTTP). Ví dụ: `background-image: url('data:image/svg+xml;charset=US-ASCII,...');`                                                                                                                                                            |
| `background-repeat`, `background-position`, `background-size` | Kết hợp với `background-image` để kiểm soát vị trí và kích thước của mũi tên tùy chỉnh.\<br\>- `background-repeat: no-repeat;`\<br\>- `background-position: right 10px center;` (đặt mũi tên cách lề phải 10px, căn giữa theo chiều dọc)\<br\>- `background-size: 12px auto;` (chiều rộng 12px, chiều cao tự động)                                                                                                                                         |
| `width`                                                       | Đặt chiều rộng cho select. Có thể là giá trị cố định hoặc phần trăm.                                                                                                                                                                                                                                                                                                                                                                                       |
| `cursor: pointer;`                                            | Thay đổi con trỏ chuột thành biểu tượng bàn tay khi di chuột qua, cho biết đây là một phần tử có thể tương tác.                                                                                                                                                                                                                                                                                                                                            |
| `outline: none;`                                              | Loại bỏ đường viền màu xanh/đen mặc định xuất hiện khi phần tử được focus. Nên thay thế bằng `box-shadow` hoặc `border-color` để cung cấp phản hồi hình ảnh cho người dùng.                                                                                                                                                                                                                                                                                |
| `transition`                                                  | Thêm hiệu ứng chuyển động mượt mà khi các thuộc tính CSS thay đổi (ví dụ: khi hover hoặc focus), giúp UI trông tinh tế hơn. Ví dụ: `transition: border-color 0.3s ease, box-shadow 0.3s ease;`                                                                                                                                                                                                                                                             |
| `select::-ms-expand`                                          | Một thuộc tính đặc biệt để ẩn mũi tên dropdown mặc định trên trình duyệt Internet Explorer/Edge cũ. `display: none;`.                                                                                                                                                                                                                                                                                                                                      |

---

### 🔸 3.2 Forms (`<form>`, `<input>`, `<button>`, `<label>`)

Các biểu mẫu là cầu nối quan trọng giữa người dùng và ứng dụng web, cho phép thu thập thông tin. Việc thiết kế form thân thiện và dễ sử dụng là yếu tố then chốt cho trải nghiệm người dùng.

---

#### Các thuộc tính CSS thường dùng cho các thành phần Form:

| Phần tử/Thuộc tính                                                                    | Ý nghĩa và Cách sử dụng                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| :------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`form`**                                                                            | Thường được dùng để định kiểu container chung cho form, bao gồm `padding`, `border-radius`, `box-shadow` để tạo hiệu ứng "card" cho form. Cũng có thể dùng Flexbox hoặc Grid để sắp xếp các nhóm trường (`.form-group`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **`label`**                                                                           | - `display: block;`: Đặt label thành phần tử khối để nó luôn nằm trên trường input, cải thiện khả năng đọc.\<br\>- `margin-bottom`: Tạo khoảng cách giữa label và input.\<br\>- `font-weight: bold;`, `color`: Để làm nổi bật label.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **`input[type="text"]`, `input[type="email"]`, `input[type="password"]`, `textarea`** | - `width`: Thường là `100%` hoặc một giá trị cố định, kết hợp với `box-sizing: border-box;`.\<br\>- `padding`: Tạo không gian bên trong trường, làm cho nó trông dễ chịu hơn và dễ nhập liệu.\<br\>- `border`, `border-radius`: Tùy chỉnh viền và bo tròn góc.\<br\>- `font-size`, `color`: Đảm bảo kích thước chữ dễ đọc và màu chữ phù hợp.\<br\>- **`box-sizing: border-box;`**: **Rất quan trọng\!** Đảm bảo rằng `padding` và `border` được tính vào tổng `width` của phần tử, giúp kiểm soát kích thước chính xác hơn và tránh lỗi tràn layout.\<br\>- `outline: none;`: Loại bỏ đường viền mặc định của trình duyệt khi input được focus. Nên thay thế bằng `border-color` hoặc `box-shadow` cho trạng thái focus.\<br\>- `transition`: Thêm hiệu ứng mượt mà khi tương tác (ví dụ: `transition: border-color 0.3s ease, box-shadow 0.3s ease;`).\<br\>- `placeholder-color` (CSS cũ) hoặc `:placeholder-shown` (CSS mới): Để định kiểu văn bản giữ chỗ. |
| **`textarea`**                                                                        | - Ngoài các thuộc tính trên, có thể thêm `resize: vertical;` (hoặc `horizontal`, `both`, `none`) để cho phép người dùng thay đổi kích thước hộp văn bản theo chiều dọc. `min-height` cũng hữu ích để thiết lập chiều cao tối thiểu.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **`button[type="submit"]`**                                                           | - `display: block;` và `width: 100%;`: Thường dùng để làm cho nút chiếm toàn bộ chiều rộng có sẵn.\<br\>- `padding`: Kích thước của nút.\<br\>- `background`: Có thể dùng màu đơn sắc, `linear-gradient`, hoặc `radial-gradient` để tạo hiệu ứng đẹp mắt.\<br\>- `color`: Màu chữ của nút.\<br\>- `border`, `border-radius`: Tùy chỉnh viền và bo góc.\<br\>- `font-size`, `font-weight`: Kích thước và độ đậm của chữ.\<br\>- `cursor: pointer;`: Thay đổi con trỏ chuột.\<br\>- `transition`: Tạo hiệu ứng động khi hover hoặc active.\<br\>- `transform`: Ví dụ `transform: translateY(-2px);` khi hover để tạo cảm giác "nhấc lên".\<br\>- `box-shadow`: Tạo hiệu ứng đổ bóng cho nút, có thể thay đổi khi hover/active.                                                                                                                                                                                                                                    |
| **Trạng thái tương tác**                                                              | - `:hover`: Áp dụng kiểu khi di chuột qua.\<br\>- `:focus`: Áp dụng kiểu khi phần tử được chọn (ví dụ: khi input được click để nhập).\<br\>- `:active`: Áp dụng kiểu khi phần tử đang được nhấn giữ.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
