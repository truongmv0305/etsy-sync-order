# Cany Etsy Helper

Chrome extension đồng bộ đơn hàng Etsy sang **Treesprint Admin** và đồng bộ ngược tracking number từ Treesprint về Etsy.

## Tính năng
- Gắn nhãn trạng thái cho từng order trên trang orders của Etsy: **Synced**, **Not Synced**, **Treesprint Ignored**, **Tracking Available** / **Tracking Not Available**.
- Sync order chưa có bên Treesprint: sync tất cả, sync các order được chọn hoặc sync từng order, có hỗ trợ tách item (split).
- Tự động add tracking từ Treesprint về Etsy: USPS, UPS, FedEx, DHL, Asendia USA, Asendia.
- Hỗ trợ YunExpress: tự lấy tracking USPS chặng cuối ở Mỹ từ yuntrack.com rồi mới add.

## 1. Cài đặt
1. Tải file **etsy_sync_order-v1.0.zip** ở trang [Releases](https://github.com/truongmv0305/etsy-sync-order/releases/latest) ([link tải trực tiếp](https://github.com/truongmv0305/etsy-sync-order/releases/download/v1.0/etsy_sync_order-v1.0.zip)), rồi giải nén.
2. Mở `chrome://extensions/`, bật **Developer mode** ở góc phải trên.
3. Bấm **Load unpacked** và chọn thư mục `etsy_sync_order` vừa giải nén.
4. Sau khi cài, extension tự mở trang orders của Etsy: https://www.etsy.com/your/orders/sold

> Không xoá hoặc di chuyển thư mục đã giải nén. Chrome chạy extension trực tiếp từ thư mục đó.

## 2. Nhập API key
1. Vào Treesprint Admin (https://treesprint.com/store) và lấy api key của store.
2. Mở trang orders của Etsy, click icon extension, nhập api key rồi bấm **Save**.
3. Extension gửi key lên Treesprint để kiểm tra:
   - Key hợp lệ: key được lưu lại, popup tự đóng và panel Treesprint hiện ở bên phải trang.
   - Key sai: extension báo **Invalid api key** và không lưu.

> Phải đang mở một trang Etsy thì mới lưu được key. Nếu không, extension sẽ báo **Please open an Etsy page before saving the api key**.

## 3. Sync orders (tab Sync Order)
1. Vào trang orders của Etsy. Mỗi order trên trang sẽ được gắn nhãn trạng thái.
2. Các order chưa có bên Treesprint hiện ở tab **Not Synced**. Nếu tất cả order đã được sync, extension báo **All orders were synced to Treesprint Admin**.
3. Chọn cách sync:
   - **Sync Orders**: sync tất cả order trong tab Not Synced.
   - Tick chọn một số order rồi bấm **Sync Selected Orders**: chỉ sync các order được chọn.
   - Bấm **Sync** ở từng dòng: sync riêng order đó.
4. Sync xong, các order sẽ nằm ở mục **Order Items** trên Treesprint Admin.

**Split:** trước khi sync, nhập số N vào ô bên cạnh nút **Sync**. Mỗi item của order sẽ được tách thành N item, mỗi item có qty = 1.

Lưu ý:
- Extension chỉ xử lý các order đang hiển thị trên trang Etsy hiện tại.
- Order đã hoàn tất hoặc đã huỷ trên Etsy không hiện trong danh sách.
- Order bị ignore bên Treesprint chỉ hiện nhãn **Treesprint Ignored**. Muốn sync lại thì bỏ ignore trên Treesprint Admin.

## 4. Add tracking về Etsy (tab Add Tracking)
1. Order nào đã có tracking number bên Treesprint sẽ hiện ở tab **Add Tracking**.
2. Chọn cách add tracking:
   - **Add Trackings**: add tracking cho tất cả order trong tab.
   - Tick chọn một số order rồi bấm **Add Tracks Selected Orders**: chỉ add cho các order được chọn.
   - Bấm **Add** ở từng dòng: add riêng order đó.
3. Extension tự thao tác trên Etsy: mở **Complete order**, chọn hãng vận chuyển, điền tracking number rồi xác nhận. Order chỉ được xoá khỏi bảng khi Etsy đã nhận tracking.

**Hãng vận chuyển:** lấy từ Treesprint. Nếu Treesprint không có thì extension tự nhận diện từ tracking number.

**YunExpress (tracking bắt đầu bằng `YT`):**
- Extension mở tab yuntrack.com để lấy tracking USPS chặng cuối ở Mỹ, rồi mới add về Etsy.
- Order chưa có tracking US sẽ bị loại khỏi bảng, kèm thông báo **order without US tracking code**.
- Không được đóng tab yuntrack khi extension đang chạy.

> Khi add tracking cho nhiều order, extension xử lý lần lượt từng order. Không thao tác trên trang Etsy cho đến khi chạy xong.

## Cập nhật phiên bản mới
1. Tải file zip mới ở trang [Releases](https://github.com/truongmv0305/etsy-sync-order/releases), giải nén và ghi đè lên thư mục cũ.
2. Vào `chrome://extensions/` và bấm nút reload (↻) ở extension **Cany Etsy Helper**.
