# SOP Operasional - Adika Tirta Daya

Repository GitHub Pages untuk hosting dokumen SOP yang diakses via QR Code.

**URL Produksi:** https://sop-operation.adikatirtadaya.co.id

---

## Struktur Repository

```
├── index.html        ← landing page + QR code generator
├── CNAME             ← konfigurasi custom domain
├── files/            ← letakkan semua file dokumen di sini
│   ├── dokumen1.pdf
│   ├── dokumen2.pdf
│   └── dokumen3.pdf
└── README.md
```

---

## Setup Awal (lakukan sekali)

### 1. Buat Repository di GitHub

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

### 2. Aktifkan GitHub Pages

1. Buka repository di GitHub → **Settings** → **Pages**
2. Di bagian **Source**, pilih branch `main` dan folder `/ (root)`
3. Klik **Save**
4. Di bagian **Custom domain**, isi `sop-operation.adikatirtadaya.co.id` lalu klik Save
5. Centang **Enforce HTTPS** (muncul setelah DNS terverifikasi, tunggu ~30 menit)

### 3. Konfigurasi DNS

Di panel DNS domain `adikatirtadaya.co.id`, tambahkan record berikut:

| Type  | Name            | Value                    | TTL  |
|-------|-----------------|--------------------------|------|
| CNAME | sop-operation   | `<username>.github.io`   | 3600 |

> Ganti `<username>` dengan username GitHub kamu.
> Propagasi DNS bisa memakan waktu 5–60 menit.

---

## Menambah Dokumen Baru

1. Upload file ke folder `files/` (PDF, gambar, Word, Excel — semua didukung)
2. Buka `index.html`, cari array `FILES`, tambahkan baris baru:

```javascript
const FILES = [
  { name: "SOP Dokumen 1", filename: "dokumen1.pdf", desc: "Deskripsi..." },
  { name: "SOP Dokumen 2", filename: "dokumen2.pdf", desc: "Deskripsi..." },
  // ↓ tambahkan di sini
  { name: "SOP Dokumen 4", filename: "dokumen4.pdf", desc: "Deskripsi baru" },
];
```

3. Commit dan push:

```bash
git add files/dokumen4.pdf index.html
git commit -m "tambah dokumen4"
git push
```

GitHub Pages akan otomatis update dalam ~1 menit.

---

## URL Format Dokumen

Setiap file yang diupload ke `files/` otomatis dapat diakses di:

```
https://sop-operation.adikatirtadaya.co.id/files/<nama-file>
```

Contoh:
- `https://sop-operation.adikatirtadaya.co.id/files/dokumen1.pdf`
- `https://sop-operation.adikatirtadaya.co.id/files/foto-produk.jpg`

---

## Tips

- **Nama file**: hindari spasi, gunakan tanda `-` atau `_` (contoh: `sop-kebersihan.pdf`)
- **Print QR**: buka halaman utama, klik tombol "Print Semua QR" untuk cetak semua QR sekaligus
- **File besar**: GitHub Pages memiliki batas ukuran file **100 MB** per file dan **1 GB** total repository