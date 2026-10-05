Bài 1 — Khôi phục commit bằng Git Reflog

Quy trình
Tạo một commit có file feature.txt, sau đó giả lập thao tác nhầm bằng git reset --hard HEAD~1. Commit không còn nằm trên nhánh nên git log --oneline không hiển thị nó; dữ liệu vẫn có thể truy ra trong reflog cục bộ.

git log --oneline
git reflog
Tìm dòng có thông điệp Them tinh nang quan trong, xác nhận hash của commit đó rồi khôi phục đúng commit bằng:

git reset --hard <commit-hash-tu-reflog>
git log --oneline
git status
reset --hard sẽ thay nội dung working tree và index. Bài thực hành chỉ dùng trong repository riêng, không có thay đổi ngoài thư mục này. Reflog là nhật ký tham chiếu local; cần khôi phục trước khi entry bị dọn bởi chính sách expire/garbage collection.

Kết quả repository này
Reflog tìm thấy 5591ab9 HEAD@{1}: commit: Them tinh nang quan trong. Khôi phục bằng git reset --hard 5591ab9; git log --oneline sau đó hiển thị lại commit 5591ab9 và file feature.txt.
