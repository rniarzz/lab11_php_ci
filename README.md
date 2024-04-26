<h1 <p align="center"><b>Praktikum 11</b></p></h1> 

**Nama: Rini Ariza**

**NIM: 312210337**

**Kelas: TI.22.A3**

---


# <p align="center">Praktikum11 : PHP FRAMEWORK (CODEIGNITER)</p>

# Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.
   
2. Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)
  
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

# Langkah-langkah praktikum

Sebelum memulai menggunakan Framework codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu di aktifkan untuk kebutuhan pengembangan Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan:

  -  php-json ekstension untuk bekerja dengan JSON;
  -  php-mysqlnd native driver untuk MySQL
  -  php-xml ekstension untuk bekerja dengan XML;
  -  php-intl ekstensi untuk membuat aplikasi multibahasa;
  -  libcurl (opsional), jika ingin pakai Curl.

## MEMBUAT FOLDER BARU

Pertama, buatlah folder baru dengan nama ```lab11_php_ci``` pada root directory web server(c:xampp/htdocs/Lab11Web)

Kemudian, sebelum memulai menggunakan Framework Codeigniter kita perlu melakukan konfigurasi dan juga mengaktifkan beberapa ekstentsi PHP seperti php-jose, php-mysqlnd, php-mxl, php-intl, dan libcurl.

## PENGAKTIFAN EKSTENSI DENGAN XAMPP CONTROL PANEL

Untuk dapat mengaktifkannya kalian perlu masuk kedalam control panel xampp kemudian pada bagian apache klik Config > ```PHP (php.ini)``` seperti gambar dibawah.

![Screenshot (568)](https://github.com/roswanda11/lab11web/assets/115516632/9d68971b-27a8-43ab-b6ac-e21931b10944)

Setelahnya cukup hilangkan tanda ; pada ekstentsi yang akan diaktifkan seperti gambar dibawah. Kemudian simpan kembali file tersebut dan restart Apache web servernya.

![Screenshot (569)](https://github.com/roswanda11/lab11web/assets/115516632/1fdebb0c-eca4-40c5-829a-fe03c4326ec2)

## PENGINSTALLAN CODEIGNITER 4

Untuk melakukan instalasi codeigniter 4 dapat dilakukan dengan dua cara , yaitu cara manual dan menggunakan composer. pada praktikum ini kita menggunakan cara manual.

  -  Unduh Codeigniter dari website https://codeigniter.com/download
  -  Extrak file zip Codeigniter ke directori htdocs/lab11_ci.
  -  Ubah nama direktory framework-4.x.xx menjadi ci4
  -  Buka browser dengan alamat http://localhost/Lab11Web/lab11_php_ci/ci4/public/

![Screenshot (948)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/82953612-1fc3-4283-8159-87571c987529)

Pilih codeigniter 4 kemudian tekan download dan tunggu hingga terinstall.

## PROSES MENJALANKAN CLI (COMMAND LINE INTERFACE)

Codeigniter 4 menyediakan CLI untuk dapat mempermudah proses development. Untuk mengakses CLI bukalah terminal/command prompt. Kemudian arahkan lokasi direktori sesuai dengan direktori kerja project dibuat. (xampp/htdocs/Lab11Web/Lab11_php_ci/ci4)

![Screenshot (953)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/58a8eb93-3c0b-4c77-bbec-ff1e1914f757)

Dan masukan perintah dibawah untuk dapat menjalankan guna memanggil CLI Codeigniter.

```php
php spark
```
![Screenshot (949)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/4c044d5d-c942-4827-97a4-2d0cbd1538ae)

## PENGAKTIFAN MODE DEBUGGING

Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. Secara default fitur ini belum aktif. 

Maka untuk mengaktifkannya, Pertama ubahlah file env menjadi .env . Kemudian ubah nilai konfigurasi pada environment variable CI_ENVIRONMENT menjadi development seperti gambar berikut.

![Cuplikan layar 2024-04-26 120325](https://github.com/rniarzz/lab11_php_ci/assets/115542704/fbc6600f-c8ff-4f92-aa2d-450f15eef418)

Selanjutnya hilangkanlah ; pada akhir kode ketika kalian membuka file app/Controller/Home.php seperti berikut.

![Cuplikan layar 2024-04-26 120751](https://github.com/rniarzz/lab11_php_ci/assets/115542704/016aac79-8e36-46c3-bd64-27d219a304cf)


Dan terjadilah error pada aplikasi yang akan ditampilkan pesan kesalahan seperti berikut.

![Screenshot (950)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/0dee292a-da87-4092-be2a-c0c53b1c6b64)

## PEMBUATAN ROUTE BARU

Untuk menambahkan route baru cukup tambahkan kode berikut.

```php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```

Kemudian buka CLI dan jalankan perintah tersebut. Jika mendapat tampilan seperti dibawah maka penambahan routes sudah benar.

![Cuplikan layar 2024-04-26 115306](https://github.com/rniarzz/lab11_php_ci/assets/115542704/fb45a354-6be2-4f4b-b812-71e7e7c27c4e)

## MEMBUAT CONTROLLER

Selanjutnya adalah membuat Controller Page seperti diatas. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.

```php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "INI HALAMAN ABOUT";
    }
    public function contact()
    {
        echo "INI HALAMAN CONTACT";
    }
    public function faqs()
    {
        echo "INI HALAMAN FAQ";
    }
}
```

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah
dapat diakses.

![lab 7 (1)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/6c88c8b8-515a-4bb3-a51b-1f269deb1d81)

## AUTO ROUTING

Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroutenya dapat diubah menggunakan nilai variabelnya. Dan ntuk menonaktifkannya ubah nilai true menjadi false.

```php
$routes->setAutoRoute(true);
```

Tambahkan method baru pada Controller Page seperti berikut.

public function tos()
{
echo "ini halaman Term of Services";
}

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan
alamat: http://localhost:8080/page/tos

![lab 7 (2)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/234b19c8-8441-4f0f-9289-033d9f2d9f8b)

## MEMBUAT VIEW

![lab 7 (3)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/18ed9e6a-82fc-4b7d-8ad4-8099f0c31dde)

Selanjutnya adalah membuat view untuk tampilan web agar lebih menarik seperti diatas dengan membuat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.

```php
public function about()
{
   return view('about', [
      'title' => 'Halaman Abot',
      'content' => 'Ini adalah halaman abaut yang menjelaskan tentang isi
halaman ini.'
   ]);
}
```

## MEMBUAT LAYOUT WEB DENGAN CSS

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Hanya saja yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Pertama, buatlah file css pada direktori public dengan nama style.css lalu buat juga folder pada direktori view yang didalamnya diisi dengan file header.php dan juga footer.php

Isi bagian header dengan kode berikut.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
    <header>
        <h1>Layout Sederhana</h1>
    </header>
    <nav>
        <a href="<?= base_url('/');?>" class="active">Home</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/about');?>">About</a>
        <a href="<?= base_url('/contact');?>">Kontak</a>
    </nav>
<section id="wrapper">
    <section id="main">
```

Dan isi bagian footer dengan kode berikut.
```php
</section>
    <aside id="sidebar">
        <div class="widget-box">
            <h3 class="title">Widget Header</h3>
            <ul>
                <li><a href="#">Widget Link</a></li>
                <li><a href="#">Widget Link</a></li>
            </ul>
        </div>
        <div class="widget-box">
            <h3 class="title">Widget Text</h3>
            <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada
tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis.
Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
        </div>
    </aside>
</section>
<footer>
    <p>&copy; 2022 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>
```

Selanjutnya, ubahlah file about pada app view dengan kode berikut.

```php
<?= $this->include('template/header'); ?>

<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>

<?= $this->include('template/footer'); ?>
```

Maka ketika halaman web tersebut kalian refresh, kalian akan mendapat tampilan seperti gambar dibawah ini.

![lab 7 (4)](https://github.com/rniarzz/lab11_php_ci/assets/115542704/7335d7b5-3b38-453b-bb89-0879ce626693)
