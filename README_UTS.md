# README UTS – Praktikum Pemrograman Perangkat Bergerak
- Nama: Zakiyyah Maulidana Salsabil
- Program Studi: D4 Teknologi Rekayasa Perangkat Lunak
- Mata Kuliah: Praktikum Pemrograman Perangkat Bergerak
- Tahun Akademik: 2026/2027

## 1. Jawaban Teori Soal 1–5

### soal 1 – Daftar Tugas dan UI Responsif

Aplikasi Tugas Praktikum dirancang supaya tetap nyaman digunakan pada ukuran layar yang berbeda. Di halaman utama, pengguna bisa melihat nama tugas, mata kuliah, serta tanda yang menunjukkan apakah tugas sudah selesai. Jumlah tugas juga ditampilkan dalam bagian ringkasan. Apabila belum ada tugas yang dimasukkan, halaman akan menampilkan kondisi daftar kosong. Saya menggunakan LayoutBuilder untuk menyesuaikan susunan kartu dengan lebar layar. Pada layar yang lebih kecil, kartu disusun satu kolom, sedangkan pada layar tablet dengan lebar minimal 700 piksel, kartu disusun menjadi dua kolom.

### Soal 2 – Form, Validasi, dan Navigasi

Penambahan tugas dilakukan melalui halaman form yang menyediakan kolom judul tugas dan mata kuliah. Pengguna tidak dapat menyimpan tugas apabila salah satu kolom belum diisi dengan benar. Fungsi trim() digunakan untuk membuang spasi yang berada di bagian awal dan akhir teks. Untuk membuka halaman tambah tugas, aplikasi menggunakan Navigator.push(). Setelah data valid, Navigator.pop() digunakan untuk mengirimkan tugas kembali ke halaman daftar. Jika pengguna memilih Batal, aplikasi kembali ke halaman sebelumnya tanpa menambahkan tugas baru.

### Soal 3 – State dan Interaksi Daftar

State berperan dalam menjaga agar informasi yang tampil selalu mengikuti perubahan data. Contohnya, setelah pengguna memasukkan tugas baru, daftar perlu diperbarui agar tugas tersebut langsung terlihat. Status pengerjaan juga dapat diubah dari belum selesai menjadi selesai, atau sebaliknya. Setiap perubahan status tercermin pada tampilan kartu dan perhitungan ringkasan. Dengan demikian, informasi pada halaman utama tidak hanya menjadi tampilan statis, tetapi ikut berubah berdasarkan tindakan pengguna.

### Soal 4 – Operasi Asynchronous dan State UI

Pembacaan data tugas dilakukan melalui proses asynchronous agar aplikasi dapat menangani proses pemuatan data dengan baik. Dalam penerapannya, Future serta async/await digunakan untuk menjalankan dan menunggu proses tersebut. Selama data belum selesai dimuat, pengguna perlu melihat indikator loading. Jika pemuatan berhasil, aplikasi menampilkan daftar tugas atau informasi bahwa belum ada data. Apabila terjadi kegagalan, aplikasi menyediakan pesan error beserta tombol Coba Lagi agar proses pemuatan dapat diulang.

### Soal 5 – Penyimpanan Lokal dan Pengujian

Agar data tugas dapat digunakan kembali, aplikasi memanfaatkan SharedPreferences sebagai penyimpanan lokal pada perangkat. Data tugas dikonversi menjadi format JSON menggunakan jsonEncode() sebelum disimpan. Ketika data dibaca, jsonDecode() digunakan untuk menguraikan JSON, kemudian Task.fromJson() mengubahnya kembali menjadi objek Task. Status penyelesaian tugas juga perlu ikut dipertahankan. Untuk memastikan mekanisme ini berjalan dengan benar, aplikasi harus diuji dengan menambahkan tugas, mengubah statusnya, kemudian menutup dan membuka aplikasi kembali. Hasil pengujian menentukan apakah penyimpanan sudah berfungsi sesuai kebutuhan.

## 2. Cara Menjalankan Aplikasi
Aplikasi dibuat menggunakan Flutter dan berada di folder D:\starter-uts.
Langkah menjalankan aplikasi:

1. Buka Visual Studio Code atau terminal.

2. Masuk ke folder proyek:
   - cd D:\starter-uts

3. Siapkan package yang dibutuhkan:
   - flutter pub get

4. Periksa perangkat atau emulator yang tersedia:
   - flutter devices

5. Jalankan aplikasi:
   - flutter run
   
6. Periksa kode untuk mengetahui apakah masih ada error:
   - flutter analyze
   
7. Menguji aplikasi dengan layar telepon lebar 360 piksel dan tablet dengan lebar minimal 700 piksel.

## 3. Hasil Acceptance Criteria

### A. Tampilan telepon 360 piksel
Tampilan aplikasi menyesuaikan lebar layar menggunakan LayoutBuilder. Jika layar kurang dari 700 piksel, daftar tugas ditampilkan dalam satu kolom. Tampilan pada lebar 360 piksel perlu dicek lagi untuk memastikan tidak ada bagian yang terpotong.



### B. Tampilan tablet minimal 700 piksel
Jika lebar layar mencapai 700 piksel atau lebih, daftar tugas ditampilkan dalam dua kolom. Tampilan pada emulator tablet perlu dicek untuk memastikan susunan tugas tetap rapi.

### C. Form dan validasi
Judul dan mata kuliah harus diisi sebelum tugas disimpan. Penggunaan trim() agar input yang hanya berisi spasi tidak dianggap valid. Ini perlu diperiksa melalui pengujian form.

### D. Navigasi
Navigasi menggunakan Navigator.push() untuk membuka halaman dan Navigator.pop() untuk kembali ke halaman sebelumnya. Tombol Simpan digunakan untuk mengembalikan data tugas ke daftar, sedangkan tombol Batal tidak boleh menambahkan tugas. Hasilnya harus diuji kembali.

### E. State dan interaksi
Aplikasi menampilkan daftar tugas dan status selesai atau belum selesai. Penambahan tugas, perubahan status, dan pembaruan jumlah tugas perlu diuji untuk memastikan berubah sesuai tindakan pengguna.

### F. Asynchronous dan tampilan kondisi aplikasi
Aplikasi menggunakan proses asynchronous untuk memuat data. Loading, daftar kosong, data berhasil dimuat, dan kondisi error perlu diuji. Tombol Coba Lagi juga perlu diperiksa apakah dapat memuat data kembali.

### G. Penyimpanan data
Saya mengerjakan TODO 2a untuk membaca data tugas dari SharedPreferences. TODO 2b untuk menyimpan data dan TODO 2c untuk menghapus data belum saya kerjakan. Oleh karena itu, fitur penyimpanan dan penghapusan data masih perlu dilengkapi dan diuji.

### H. Pemeriksaan aplikasi
Pemeriksaan dilakukan menggunakan flutter analyze dan pengujian pada emulator. Hasil pemeriksaan akan dilihat sesuai tampilan yang sebenarnya. 

## 4. Ringkasan Satu Alur Kode
1. Saat aplikasi dibuka, TaskListScreen memanggil TaskStorage.load() untuk mengambil data tugas dari SharedPreferences.
2. Data yang tersimpan dalam bentuk JSON dibaca menggunakan jsonDecode(), lalu diubah menjadi objek Task dengan Task.fromJson() agar bisa ditampilkan di daftar tugas.
3. Saat data disimpan, Task.toJson() mengubah tugas menjadi Map, kemudian jsonEncode() mengubahnya menjadi JSON untuk disimpan ke SharedPreferences.

## 5. Penyesuaian Gradle
Project awal menggunakan Gradle 8.10.2, tetapi versi tersebut belum memenuhi kebutuhan Flutter 3.47.1. Jadi, versi Gradle perlu diperbarui agar sesuai dengan kebutuhan Flutter. Perubahan ini dilakukan pada pengaturan Gradle, tanpa mengubah kode Dart.

## 6. Error yang Tersisa dan Bagian yang Belum Selesai
1. Penyimpanan data: Saya baru mengerjakan TODO 2a untuk membaca data. TODO 2b dan TODO 2c belum dikerjakan.
2. Data tugas: Data yang baru ditambahkan atau diubah belum tentu tersimpan setelah aplikasi ditutup karena fungsi penyimpanan belum dilengkapi.
3. Pemeriksaan kode: Saya perlu menjalankan flutter analyze untuk memastikan tidak ada error.
4. Pengujian fitur: Tampilan telepon dan tablet, form, navigasi, perubahan status, loading, dan penanganan error masih perlu diperiksa kembali.

## Kesimpulan
Secara keseluruhan, bagian pengerjaan data lokal telah berjalan sebagian. Saya sudah menyelesaikan TODO 1a untuk mengonversi data tugas ke format JSON serta TODO 2a untuk membaca data tersimpan dari SharedPreferences saat aplikasi pertama kali dibuka.
Namun, pengerjaan belum sepenuhnya selesai karena TODO 2b (proses menyimpan perubahan data ke penyimpanan lokal) dan TODO 2c (proses menghapus data tugas) belum diimplementasikan. Akibatnya, data baru yang ditambahkan atau status tugas yang diubah belum bisa tersimpan secara permanen ketika aplikasi ditutup dan dibuka kembali.