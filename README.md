# Social Network Application

## Cách chạy ứng dụng với Docker Compose

### Yêu cầu
- Docker
- Docker Compose

### Các bước chạy

1. **Clone repository và di chuyển vào thư mục gốc:**
```bash
cd social-network
```

2. **Build và chạy tất cả services:**
```bash
docker-compose up -d --build
```

3. **Kiểm tra trạng thái containers:**
```bash
docker-compose ps
```

### Các services sẽ chạy trên:

- **Frontend (React)**: http://localhost:3000
- **API Backend (Node.js)**: http://localhost:4000  
- **MongoDB**: localhost:6364
- **Redis**: localhost:6363

### Các lệnh hữu ích

**Xem logs:**
```bash
# Xem tất cả logs
docker-compose logs

# Xem logs của service cụ thể
docker-compose logs api
docker-compose logs client
docker-compose logs mongodb
docker-compose logs redis
```

**Dừng services:**
```bash
docker-compose down
```

**Dừng và xóa volumes (xóa data):**
```bash
docker-compose down -v
```

**Restart một service:**
```bash
docker-compose restart api
docker-compose restart client
```

### Cấu trúc thư mục sau khi setup:

```
social-network/
├── docker-compose.yml          # File chính để chạy toàn bộ app
├── api_socialNetwork/         # Backend Node.js
│   ├── Dockerfile
│   ├── package.json
│   └── ...
├── client_socialNetwork/      # Frontend React
│   ├── Dockerfile
│   ├── package.json
│   └── ...
└── README.md
```

### Lưu ý
- Lần đầu chạy sẽ mất thời gian để download images và build
- MongoDB sẽ tạo database `social_network_db` với user `admin` và password `password123`
- Data sẽ được lưu trong Docker volumes và không mất khi restart containers
- Client React chạy development server trên port 3000
- API backend chạy trên port 4000