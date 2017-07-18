# mnist-malab
Demo môn học nhận dạng thị giác và ứng dụng

Dữ liệu của bài toán nhận dạng chữ viết tay được lấy từ:
http://yann.lecun.com/exdb/mnist/index.html

Sau khi get dữ liệu thì ta sẽ có 4 file gồm hình ảnh và nhãn của data train và data test ở thư mục data.


Ở thư mục model là nơi lưu trữ các model tương ứng khi thự hiện train xong. Việc lưu trữ này nhằm mục đích load model lên khi thực hiện test.

Ngoài ra về việc load ảnh và nhãn của bộ dữ liệu MNIST có sử dụng câu lệnh được phát triển bởi đại học Standford theo đường dẫn bên dưới:
http://ufldl.stanford.edu/wiki/resources/mnistHelper.zip

Chương trình chính gồm 2 file bào gồm file main.fig chứ các thành phần GUI và file main.h chứa các thành phần thực hiện chương trình

Xử lí chính:
Phần GUI
Khi tạo xong file GUI thì matlab sẽ tự động tạo 1 file .m có tên giống với tên file GUI với các fuction rỗng được xây dựng sẵn để người dùng implement.
Ở GUI này sẽ 2 popup cho phép người dùng chọn đặc trưng (raw, HOG, LBP) và chọn phương pháp ML (KNN, SVM)
Tiếp đến sẽ có 2 nút Train và Test tương ứng cho việc thực hiện train và test tương ứng với đặc trưng và thuật toán ML người dùng đã chọn

Phần train
Khi thực hiện train, sẽ thay đổi status để người dùng biết ứng dụng đang thực hiện việc gì.
Sau đó sẽ load bộ dữ liệu train lên, từ feature đã được lựa chọn ở GUI, ta sẽ thực hiện trích xuất model tương ứng. Ở demo thì em có thêm một số option khi trích xuất đặc trưng. HOG em sử dụng thêm thông số Cellsize là 8x8. LBP em sử dụng NumNeighbors là 8 và Radius là 4.
Sau khi đã trích xuất xong đặc trưng, dựa vào các option người dùng đã chọn em thực hiện xây dựng Model, sau khi xây dựng xong sẽ save lại vào các thư mục con tương ứng trong thư mục model. Cuối cùng thông báo cho người dùng quá trình train đã thành công.

Phần test
Khi thực hiện test, sẽ thực hiện thay đối trạng thái để người dùng biết ứng dụng đang thực thi, sau đó load datatest.
Dựa và các option người dùng chọn ở GUI, chương trình sẽ load các model được lưu ở thư mực tương ứng, tiếp theo là trích xuất đặc trưng của datatest và thực hiện predict.
Cuối cùng khi predict xong sẽ hiển thị tỉ lệ chính xác của thuật toán và thay đổi trạng thái test thành công
