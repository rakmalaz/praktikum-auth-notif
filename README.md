# Praktikum Autentikasi JWT dan Push Notification

Pemrograman Mobile (SIF125113) - Program Studi Sistem Informasi, UIN Sunan Ampel Surabaya

Disusun oleh: Rayhan Akmal Azhari (09020625073)
Dosen pengampu: Ahmad Yusuf, M.Kom

Aplikasi kecil dengan akun pengguna, login memakai JSON Web Token (JWT), endpoint privat, penyimpanan token di penyimpanan aman perangkat, dan push notification yang dikirim dari backend.

## Struktur repository

| Folder | Isi |
| --- | --- |
| `api-auth-notif` | Backend Express + MySQL (register, login, JWT, push token) |
| `mobile-auth-notif` | Aplikasi React Native dengan Expo |

## Teknologi

- Backend: Node.js, Express, mysql2, bcrypt, jsonwebtoken, dotenv, cors
- Database: MySQL/MariaDB (XAMPP)
- Mobile: React Native, Expo Router, expo-secure-store, expo-notifications
- Notifikasi: Expo Push Service dengan FCM v1 (Android)

## Endpoint API

| Metode | URL | Auth | Keterangan |
| --- | --- | --- | --- |
| POST | `/auth/register` | Tidak | Daftar akun baru |
| POST | `/auth/login` | Tidak | Login, mengembalikan JWT |
| GET | `/auth/me` | Bearer JWT | Profil pengguna yang login |
| POST | `/notifications/token` | Bearer JWT | Simpan ExpoPushToken perangkat |
| POST | `/notifications/test` | Bearer JWT | Kirim notifikasi uji |

## Menjalankan backend

1. Nyalakan MySQL di XAMPP, lalu impor `api-auth-notif/schema.sql` untuk membuat database dan tabel.
2. Salin `.env.example` menjadi `.env`, lalu isi nilainya (port database, user, password, JWT_SECRET).
3. Jalankan:

```bash
cd api-auth-notif
npm install
node server.js
```

## Menjalankan aplikasi mobile

Push notification di Android memerlukan development build, tidak dapat diuji di Expo Go.

```bash
cd mobile-auth-notif
npm install
npx expo start --dev-client
```

Sesuaikan alamat backend pada `src/services/api.js` dengan alamat komputer yang menjalankan API.

## Keamanan

File `.env` dan kunci service account Firebase sengaja tidak disertakan dalam repository ini. Gunakan `.env.example` sebagai acuan variabel yang perlu diisi.
