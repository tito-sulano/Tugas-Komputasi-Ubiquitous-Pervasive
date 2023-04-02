**Nama        : Tito Sulano**

**NIM         : 09021282025050**

**Mata kuliah : Komputasi Ubiquitos dan Perpasiv**

**Kelas       : Teknik Informatika**

**Semester    : 6 (Enam)**

**Fakultas Ilmu Komputer, Universitas Sriwijaya.**

# Lab-1: Implementasi dan pemanfaatan infrastruktur perangkat keras menggunakan ownCloud pada Sistem operasi linux Ubuntu 18.04 server

Tujuan : 
* Mahasiswa bisa mengimplementasikan sistem operasi berbasis web interface, pemanfaatan storage berbasis cloud.

## Perkenalan.
Owncloud adalah sebuah platform file sharing yang bersifat open-source dan berbagai gabungan atau kolaborasi yang dapat menyimpan, memanage personal content kita, seperti dokumen dan gambar pada lokasi yang terpusat. Implementasi dari ownCloud merupakan hal yang serupa pada aplikasi dropbox, dengan fitur online storage yang dapat kita create sesuai dengan resource pada server atau komputer kita. 

## Langkah 1 - Installasi Ubuntu Server.
Pertama kali, kita harus mendownload file .iso linux ubuntu server pada link berikut https://ubuntu.com/download/server

![image](https://user-images.githubusercontent.com/79504944/229356100-28daa134-2eb4-4f05-b4d9-e5e45e269865.png) 
 
Lakukan instalasi di komputer yang tersedia, ataupun jalankan menggunakan software virtualisasi seperti virtualbox (https://www.virtualbox.org/wiki/Downloads) ataupun opsitional menggunakan VM-ware player (https://www.vmware.com/go/downloadworkstationplayer). Untuk tutorial tata cara proses instalasi ubuntu server pada aplikasi virtualisasi akan dilewatkan.
*Catatan: pastikan alamat IP pada virtualbox terpasang dan dalam network yang sama.

## Langkah 2 - Installasi ownCloud
Paket ownCloud server pada dasarnya tidak tersedia pada repositori dari sistem linux ubuntu tersebut, maka perlu kita unduh release key menggunakan curl command dan import menggunakan apt-key add, seperti pada command di bawah:

`$ curl https://download.owncloud.org/download/repositories/10.0/Ubuntu_18.04/Release.key | sudo apt-key add -`

![image](https://user-images.githubusercontent.com/79504944/229356654-455feb89-6e31-4ef3-a87b-1c6be823ae62.png)

File ‘Release.key’ berisikan sebuah PGP (Pretty Good Privacy publik key seperti apt, yang akan digunakan untuk men-verifikasi ownCloud package sebagai aplikasi authentic.
Untuk tambahan silahkan tambahkan owncloud.list pada source.list.d pada direktori apt.

`$ echo 'deb http://download.owncloud.org/download/repositories/10.0/Ubuntu_18.04/ /' | sudo tee /etc/apt/sources.list.d/owncloud.list`

![image](https://user-images.githubusercontent.com/79504944/229356633-581120f2-0341-4394-bb46-809bb752f1b6.png)

Kemudian lakukan update, instalasi beberapa paket - paket pendukung seperti php

`$ sudo apt update`

![image](https://user-images.githubusercontent.com/79504944/229356788-744d5867-bd12-4022-83dd-b6fc80c22da2.png)

`$ sudo apt install php-bz2 php-curl php-gd php-imagick php-intl php-mbstring php-xml php-zip owncloud-files`

![image](https://user-images.githubusercontent.com/79504944/229356837-ca115cd9-debf-462b-825a-144bae0ef440.png)

## Langkah 3 - konfigurasi MySQL database
Login ke database sql server menggunakan command line sebagai berikut:

`$ sudo mysql`

Lakukan konfigurasi untuk password MySQL pada akun root:

`$ mysql -u root -p`

Kemudian, buatlah database untuk ownCloud:

`$ mysql> CREATE DATABASE owncloud;`

`$ mysql> GRANT ALL ON owncloud.* to 'owncloud'@'localhost' IDENTIFIED BY 'owncloud_database_password';`

*Catatan: ganti owncloud_database_password dengan password database.

`$ mysql> FLUSH PRIVILEGES;`

`$ mysql> exit`

## Langkah 4 - konfigurasi ownCloud
Untuk melakukan akses pada ownCloud web interface, bukalah browser anda, dan akses http://alamat_ip_server/
Kita akan melihat konfigurasi ownCloud pada browser, buatlah akun anda, dan password:

![image](https://user-images.githubusercontent.com/79504944/229356318-1d560472-6c4c-4228-883a-7e7e0ac4f61d.png)

Selanjutnya lewati, konfigurasi Data folder kemudian lanjutkan ke konfigurasi database.

![image](https://user-images.githubusercontent.com/79504944/229356332-b7d2af27-039e-4aea-bb93-e1c13d5bdafa.png)

Kemudian klik Finish untuk menyelesaikan tahapan konfigurasi ownCloud. Lakukan login menggunakan akses akun dan password yang kita buat sebelumnya.

![image](https://user-images.githubusercontent.com/79504944/229356340-cd21d088-f63c-46cd-9dc9-1b7516e4797a.png)

Setelah itu kita akan ditampilkan, tampilan dari ownCloud tersebut.

![image](https://user-images.githubusercontent.com/79504944/229356353-8fd4eee6-33d9-4eda-9dfe-974681ecb757.png)

Note: ulangi langkah - langkah di atas, kemudian jelaskan fitur - fitur yang ada owncloud tersebut, beserta pemanfaatannya.
