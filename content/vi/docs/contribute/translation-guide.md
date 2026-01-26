# Hướng dẫn dịch Kubernetes Glossary sang Tiếng Việt

Tài liệu này giải thích các nguyên tắc và lý do đằng sau các bản dịch glossary của Kubernetes. Dành cho người mới bắt đầu contribute vào dự án dịch thuật.

---

## 📋 Mục lục

1. [Nguyên tắc dịch thuật chung](#nguyên-tắc-dịch-thuật-chung)
2. [Giải thích từng thuật ngữ đã dịch](#giải-thích-từng-thuật-ngữ-đã-dịch)
3. [Các thuật ngữ KHÔNG nên dịch](#các-thuật-ngữ-không-nên-dịch)
4. [Tips cho người mới](#tips-cho-người-mới)

---

## 🎯 Nguyên tắc dịch thuật chung

### 1. Giữ nguyên thuật ngữ kỹ thuật phổ biến
Các thuật ngữ đã được cộng đồng IT Việt Nam sử dụng rộng rãi thì **KHÔNG dịch**:
- `Pod`, `Container`, `Node`, `Cluster`, `API`, `Controller`
- `Namespace`, `Label`, `Annotation`, `Selector`
- `ConfigMap`, `Secret`, `Volume`, `Service`

**Lý do:** Dịch sẽ gây khó hiểu vì người dùng đã quen với thuật ngữ gốc.

### 2. Dịch phần mô tả, giải thích
Phần `short_description` và nội dung chính **NÊN dịch** để người Việt dễ hiểu.

### 3. Giữ nguyên cú pháp Hugo/Markdown
```markdown
{{< glossary_tooltip text="container" term_id="container" >}}
```
Phần này là shortcode của Hugo, **KHÔNG được thay đổi**.

### 4. Giữ nguyên metadata
Các trường `id`, `date`, `full_link`, `tags` **KHÔNG được thay đổi**.

---

## 📖 Giải thích từng thuật ngữ đã dịch

### 1. `cluster-operator.md` - Người vận hành Cluster

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Cluster Operator | Người vận hành Cluster | "Operator" ở đây là **người**, không phải Kubernetes Operator pattern |
| configures, controls, and monitors | cấu hình, kiểm soát và giám sát | Dịch động từ thành tiếng Việt tự nhiên |
| maintenance activities | hoạt động bảo trì | Thuật ngữ phổ biến trong IT |
| Operator pattern | Operator pattern | **KHÔNG dịch** vì đây là tên riêng của design pattern |

**⚠️ Lưu ý quan trọng:**
```markdown
{{< note >}}
Người vận hành cluster khác với [Operator pattern](/vi/docs/...)
{{< /note >}}
```
Đoạn này phân biệt giữa **người** (cluster operator) và **pattern** (Kubernetes Operator).

---

### 2. `volume.md` - Volume

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Volume | Volume | **KHÔNG dịch** - đây là thuật ngữ chuẩn |
| directory containing data | thư mục chứa dữ liệu | Dịch để giải thích khái niệm |
| container restarts | khởi động lại container | "Restarts" = khởi động lại |
| data is preserved | dữ liệu được bảo toàn | "Preserved" = được giữ lại, bảo toàn |

**Cấu trúc file:**
```yaml
title: Volume          # Giữ nguyên tiếng Anh (tên thuật ngữ)
short_description: >   # Dịch sang tiếng Việt
  Một thư mục chứa dữ liệu...
```

---

### 3. `image.md` - Image

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Image | Image | **KHÔNG dịch** - "container image" là thuật ngữ chuẩn |
| stored instance | phiên bản lưu trữ | Giải thích rõ hơn: image là 1 "bản snapshot" |
| container registry | container registry | **KHÔNG dịch** |
| metadata | metadata | **KHÔNG dịch** |
| executable | chương trình thực thi | Dịch để người mới hiểu |

---

### 4. `kube-controller-manager.md` - kube-controller-manager

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| kube-controller-manager | kube-controller-manager | **KHÔNG dịch** - đây là tên component |
| Control Plane component | Thành phần control plane | "Control plane" giữ nguyên, "component" dịch |
| controller processes | tiến trình controller | "Processes" = tiến trình |
| compiled into a single binary | biên dịch thành một binary duy nhất | Thuật ngữ lập trình |

**Tại sao giữ nguyên `kube-controller-manager`?**
- Đây là **tên chính thức** của component
- Khi chạy `kubectl`, người dùng thấy tên này
- Dịch sẽ gây nhầm lẫn khi troubleshoot

---

### 5. `limitrange.md` - LimitRange

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| LimitRange | LimitRange | **KHÔNG dịch** - đây là tên Kubernetes object |
| constraints | ràng buộc | Giới hạn, điều kiện |
| resource consumption | mức tiêu thụ tài nguyên | CPU, memory, storage |
| namespace | namespace | **KHÔNG dịch** |

---

### 6. `mirror-pod.md` - Mirror Pod

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Mirror Pod | Mirror Pod | **KHÔNG dịch** - thuật ngữ chuyên biệt |
| API server | API server | **KHÔNG dịch** |
| static pod | static pod | **KHÔNG dịch** |
| tracks | theo dõi | "Mirror" ở đây nghĩa là "phản chiếu" trạng thái |
| kubelet daemon | kubelet daemon | **KHÔNG dịch** |

**Giải thích khái niệm:**
- Static pod: Pod được kubelet quản lý trực tiếp (không qua API server)
- Mirror pod: "Bản sao" của static pod hiển thị trên API server để monitoring

---

### 7. `name.md` - Name

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Name | Name | **KHÔNG dịch** trong title |
| client-provided string | chuỗi do client cung cấp | Giải thích: người dùng đặt tên |
| resource URL | resource URL | **KHÔNG dịch** |

---

### 8. `network-policy.md` - Network Policy

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Network Policy | Network Policy | **KHÔNG dịch** - tên object |
| specification | đặc tả | Định nghĩa, mô tả cấu hình |
| network endpoints | network endpoint | **KHÔNG dịch** |
| declaratively configure | khai báo cấu hình | Declarative = khai báo (vs imperative) |
| network plugin | network plugin | **KHÔNG dịch** |
| network provider | network provider | **KHÔNG dịch** |

---

### 9. `secret.md` - Secret

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Secret | Secret | **KHÔNG dịch** - tên object (và cũng là từ phổ biến) |
| sensitive information | thông tin nhạy cảm | Passwords, tokens, keys |
| OAuth tokens | OAuth token | **KHÔNG dịch** |
| SSH keys | SSH key | **KHÔNG dịch** |
| base64 strings | chuỗi base64 | **KHÔNG dịch** base64 |
| encrypted at rest | mã hóa khi lưu trữ | "At rest" = khi ở trạng thái lưu trữ |
| volume mount | volume mount | **KHÔNG dịch** |
| environment variable | biến môi trường | Thuật ngữ phổ biến đã được dịch |
| confidential data | dữ liệu bí mật | Secret = bí mật, nhạy cảm |

---

### 10. `probe.md` - Probe

| Thuật ngữ gốc | Bản dịch | Giải thích |
|---------------|----------|------------|
| Probe | Probe | **KHÔNG dịch** - thuật ngữ chuyên biệt |
| check performed periodically | kiểm tra được thực hiện định kỳ | Kubelet check container health |
| container's state and health | trạng thái và sức khỏe của container | Liveness, readiness |
| lifecycle | vòng đời | Container lifecycle |

**Các loại Probe trong Kubernetes:**
- **Liveness Probe**: Kiểm tra container còn sống không
- **Readiness Probe**: Kiểm tra container sẵn sàng nhận traffic chưa
- **Startup Probe**: Kiểm tra ứng dụng đã khởi động xong chưa

---

## 🚫 Các thuật ngữ KHÔNG nên dịch

| Thuật ngữ | Lý do |
|-----------|-------|
| Pod, Container, Node | Rất phổ biến, ai cũng dùng |
| Namespace, Label, Annotation | Tên object/concept chuẩn |
| API, REST, HTTP | Thuật ngữ web/networking chuẩn |
| YAML, JSON | Định dạng file |
| Controller, Scheduler, Kubelet | Tên component |
| ConfigMap, Secret, Volume | Tên object |
| Ingress, Service, Endpoint | Tên object |
| Deployment, StatefulSet, DaemonSet | Tên workload |

---

## 💡 Tips cho người mới

### 1. Đọc các bản dịch đã được merge
Xem các PR đã được approve để học cách dịch:
- [kubernetes/website PRs với label `language/vi`](https://github.com/kubernetes/website/pulls?q=is%3Apr+label%3Alanguage%2Fvi)

### 2. Giữ cấu trúc file giống bản gốc
```yaml
---
title: [Giữ nguyên hoặc dịch tùy trường hợp]
id: [KHÔNG ĐỔI]
date: [KHÔNG ĐỔI]
full_link: [KHÔNG ĐỔI]
short_description: >
  [DỊCH phần này]
aka: [KHÔNG ĐỔI]
tags:
- [KHÔNG ĐỔI]
---
[DỊCH nội dung chính]
```

### 3. Test bản dịch locally
```bash
# Build Hugo site
make serve

# Truy cập http://localhost:1313/vi/docs/reference/glossary/
```

### 4. Quy trình tạo PR
1. Fork repo `kubernetes/website`
2. Tạo branch: `vi/glossary/{term-name}`
3. Thêm file vào `content/vi/docs/reference/glossary/`
4. Commit với message: `docs(vi): Add Vietnamese translation for glossary {term}`
5. Tạo PR với format:
   ```markdown
   ## Description
   - Add Vietnamese translation for {term}
   - Link: https://kubernetes.io/docs/reference/glossary/?all=true#{term}
   
   ## Issue
   NONE
   
   Closes: #
   ```

### 5. Reviewer thường kiểm tra gì?
- ✅ Cú pháp Hugo shortcode đúng
- ✅ Không dịch các thuật ngữ kỹ thuật phổ biến
- ✅ Dịch tự nhiên, không máy móc
- ✅ Giữ nguyên format và metadata

---

## 📚 Tài liệu tham khảo

- [Kubernetes Vietnamese Localization Guide](https://kubernetes.io/vi/docs/contribute/localization/)
- [Kubernetes Glossary (EN)](https://kubernetes.io/docs/reference/glossary/)
- [Hugo Shortcodes trong K8s docs](https://kubernetes.io/docs/contribute/style/hugo-shortcodes/)

---

*Tài liệu này được tạo bởi @trieungoctam - Vietnamese Kubernetes Contributors*
