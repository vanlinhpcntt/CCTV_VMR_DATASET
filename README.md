# CCTV-VMR-VN: Bộ dữ liệu Camera giám sát thực tế phục vụ bài toán Truy vấn khoảnh khắc video từ camera giám sát

[![Phiên bản](https://img.shields.io/badge/phi%C3%AAn%20b%E1%BA%A3n-v1.0-blue.svg)](https://github.com/vanlinhpcntt/CCTV_VMR_DATASET/releases/tag/v1.0)
[![Lưu trữ](https://img.shields.io/badge/Git%20LFS-18%20GB-orange.svg)](https://git-lfs.com/)
[![Bài toán](https://img.shields.io/badge/B%C3%A0i%20to%C3%A1n-Video%20Moment%20Retrieval-green.svg)](#1-tổng-quan)

## 1. Tổng quan
**CCTV-VMR-VN** là bộ dữ liệu chuẩn được xây dựng chuyên biệt cho bài toán **Truy vấn khoảnh khắc video từ camera giám sát (VMR)** và **Định vị hành động theo thời gian** trong môi trường thực tế tại Việt Nam. 

Khác với các bộ dữ liệu video miền mở phổ biến (như ActivityNet hay Charades-STA), dữ liệu từ camera giám sát (CCTV) mang những đặc thù thách thức riêng như: góc quay rộng cố định, mật độ tương tác nhiều đối tượng dày đặc, biến thiên ánh sáng theo thời gian trong ngày và các câu truy vấn mô tả hành vi chi tiết. Bộ dữ liệu này hỗ trợ trực tiếp cho các nghiên cứu về **Căn chỉnh ngữ nghĩa đa cấp độ**, **Lọc nhiễu không gian theo vùng quan tâm (ROI)** và **Tinh chỉnh biên thời gian bằng Học tăng cường (RL)** (tiêu biểu là kiến trúc **CRAC**: *CLIP + ROI + Actor-Critic*).

---

## 2. Thống kê bộ dữ liệu
* **Tổng số đoạn video sự kiện:** 4.191 video clip đã được phân đoạn theo mốc thời gian (định dạng `.mp4`).
* **Góc máy camera:** Hệ thống đa camera (`cam01`, `cam03`...) ghi hình tại nhiều bối cảnh giám sát thực tế trong nhà và ngoài trời.
* **Tổng dung lượng lưu trữ:** ~18 GB (được quản lý và đồng bộ phiên bản qua **Git LFS**).
* **Định dạng gán nhãn:** Các tệp cấu trúc JSON Lines (`.jsonl`) lưu trữ chính xác biên thời gian (`start_time`, `end_time`), nhãn sự kiện, mã camera và câu truy vấn ngôn ngữ tự nhiên mô tả hành vi.

---

## 3. Cấu trúc thư mục
Kho lưu trữ được tổ chức thành 3 thư mục chính:

```text
CCTV_VMR_DATASET/
├── ann/                     # Dữ liệu gán nhãn sự kiện thô và đã qua tiền xử lý
├── dataset/                 # Các tệp phân chia tập dữ liệu chuẩn (train.jsonl, val.jsonl, test.jsonl)
├── event_clips/             # Các đoạn video sự kiện được phân loại theo từng mã camera và bối cảnh
│   ├── cam01/
│   │   └── ...
│   └── cam03/
│       └── 19/
│           ├── 19_video6_norm_e008.mp4
│           └── all_clips_map.jsonl
├── .gitattributes           # Cấu hình theo dõi tệp dung lượng lớn của Git LFS (*.mp4, *.avi, *.zip)
└── README.md                # Tài liệu mô tả bộ dữ liệu
