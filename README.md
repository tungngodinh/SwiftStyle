Sytle này tạo ra nhằm mục đích nhất quán việc đặt tên cho các dự án. Được tham khảo từ 

[Swift.org API Design Guidelines](https://swift.org/documentation/api-design-guidelines)

[Raywenderlich Style Guide](https://github.com/raywenderlich/swift-style-guide)

## Mục tiêu hướng tới
- Sytle này tạo ra nhằm mục đích nhất quán việc đặt tên cho các dự án.
- Tránh nhầm lẫn cho người cũ, dễ sử dụng lại cho người mới bắt đầu.

## Chung
- Sự rõ ràng.
- Sử dụng camel case (e.g. CustomerModel, SettingService ...).
- Sử dụng Uppercase cho Type và Protocols, Lowercase cho phần còn lại (e.g. Property, Function, Enum case ...).
- Sử dụng tên cho vai trò thay vì loại.

## Đặt tên trong dự án
- Đặt tên có hậu tố theo group chứa chúng (trừ Protocols) (e.g. CustomreModel, CustomreService, CustomerStore, CustomerController, ...).
- Không nên thêm tiền tố modul. 

## Class
- Không thêm tiền tố của modul. Nếu các modul có chứa nhiều hơn 1 class khi sử dụng có thể gọi thêm tiền tố modul.

```swift
import SomeModule

let myClass = MyModule.UsefulClass()
let someClass = SomeModule.UsefulClass()
```

## Protocols
- Hậu tố mô tả chức năng của Protocols.
 + Danh từ able, ible hoặc ing (e.g. Equalable, ProgessReporting ...).
 + Loại Type (e.g. RowType, CellType ...).
 + Ủy nhiệm hàm (e.g. DatePickerDelegate ...).
 + Cài đặt (e.g. RowSetting, CustomViewSetting ...).

- Các Protocols dạng ủy nhiệm hàm có hậu tố là Delegate, tham số đầu tiên là nguồn của delegate (e.g. CustomerControllerDelegate ...).

### Nên
```swift
func customerController(_ controller: CustomerController, didSelect customerId: Int)
```
### Không nên

```swift
func didSelectCustomerId(controller: CustomerController, id: Int)
```

## Function
- Các hàm có hậu tố -ed, -ing là hàm không biến đổi (non-mutating).

```swift
func byAdding(newRow row: RowType) -> [RowType] {
    return self.rows + [row]
}
```
- Các hàm không chứa tiền tố hoặc có tiền tố form- là hàm thay đổi (mutating).
```swift
func sortRows() {
    self.rows.sort()
}

func formAdd(newRow row: RowType) {
    self.rows.append(row)
}
```

- Các hàm kiểu bool nên sử dụng như các xác nhận (isValidate, isHidden).
- Sử dụng thuật ngữ rõ ràng, không gây nhầm lẫn, tránh viết tắt.
- Chọn tên tham số dễ hiểu (được hiểu là khi đọc đã biết hàm làm gì).

Nên
```swift
func remove(at protison: Int)
```
Không nên
```swift
func remove(_ protison: Int)
```

- Lợi dụng các tham số mặc định.

```swift
func select(at indexPath: IndexPath, with animated: Bool = true)
```

## Unused code
- Code không còn sử dụng nên xóa.
- Code chỉ gọi tới phương thức của lớp cha cũng nên loại bỏ.

```swift
override func config() {
    supper.config()

    // Thân hàm không chứa nội dung thêm nên xóa
}
```

## Import modul cần thiết
- Chỉ import các modul sử dụng trong file.
- Những modul không còn sử dụng nên xóa khỏi import.
