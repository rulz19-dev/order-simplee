# Menu Digital

Web app menu cafe/restoran: pelanggan membuka lewat QR di meja, admin mengelola menu tanpa coding.
Teknologi: HTML + CSS + JavaScript murni. Data disimpan di **localStorage** (MVP).

## Struktur
```
menu-digital/
├── index.html      Halaman menu pelanggan (cari, filter, detail)
├── admin.html      Panel admin (login, tambah/ubah/hapus, toggle habis, statistik)
├── qr.html         Pembuat QR code per meja (siap cetak)
├── css/style.css   Gaya bersama + mode gelap
└── js/
    ├── store.js    Lapisan data (ganti isinya untuk Firebase/Supabase)
    ├── app.js      Logika halaman pelanggan
    └── admin.js    Logika panel admin
```

## Cara pakai
1. Buka `index.html` di browser (klik dua kali, atau pakai Live Server di VS Code).
2. Buka `admin.html`. Sandi awal: `admin123` — ganti di **Pengaturan**.
3. Tambah/ubah menu, unggah foto, tekan sakelar **Tersedia** untuk menandai habis; berubah langsung.
4. Buka `qr.html` setelah website online, isi alamatnya, lalu **Cetak semua** dan tempel di meja.

## Cara deploy (gratis)
- **Netlify**: buka app.netlify.com/drop, seret folder `menu-digital`. Selesai.
- **Vercel**: `npm i -g vercel`, lalu jalankan `vercel` di dalam folder.
- **GitHub Pages**: unggah ke repo, Settings → Pages → pilih branch `main`.

## Penting: batasan localStorage
Data tersimpan **per browser/perangkat**. Artinya menu yang diubah admin di laptop **tidak otomatis
terlihat** di HP pelanggan. Untuk dipakai sungguhan, pindahkan ke Firebase atau Supabase:
tulis ulang fungsi di `js/store.js` (`getMenu`, `saveItem`, `deleteItem`, `toggleAvailable`,
`addView`) — file lain tidak perlu diubah. Login admin saat ini juga hanya di sisi browser;
gunakan Firebase Auth / Supabase Auth untuk produksi.

## Menambah kategori/label
Edit `CATEGORIES` dan `TAGS` di bagian atas `js/store.js`.
