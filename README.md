<?php
/**
 * UTS OOP Presentasi
 * Nama: Ajeng Saufika
 * NIM: [Masukkan NIM Anda]
 * 
 * File: index.php
 * Berisi implementasi class parent dan 2 child class
 */

// Class Parent: Kendaraan (abstract class)
abstract class Kendaraan {
    protected $merk;
    protected $tahunProduksi;
    protected $warna;
    protected $kecepatanMaks;

    public function __construct($merk, $tahunProduksi, $warna, $kecepatanMaks) {
        $this->merk = $merk;
        $this->tahunProduksi = $tahunProduksi;
        $this->warna = $warna;
        $this->kecepatanMaks = $kecepatanMaks;
    }

    // Abstract method yang harus diimplementasikan child class
    abstract public function getSpesifikasi();

    // Method umum untuk semua kendaraan
    public function getInfoDasar() {
        return "Merk: {$this->merk}, Tahun: {$this->tahunProduksi}, Warna: {$this->warna}";
    }
}

// Child Class 1: Mobil
class Mobil extends Kendaraan {
    private $jumlahPintu;
    private $tipeBahanBakar;

    public function __construct($merk, $tahunProduksi, $warna, $kecepatanMaks, $jumlahPintu, $tipeBahanBakar) {
        parent::__construct($merk, $tahunProduksi, $warna, $kecepatanMaks);
        $this->jumlahPintu = $jumlahPintu;
        $this->tipeBahanBakar = $tipeBahanBakar;
    }

    public function getSpesifikasi() {
        return $this->getInfoDasar() . 
               ", Jumlah Pintu: {$this->jumlahPintu}" .
               ", Bahan Bakar: {$this->tipeBahanBakar}" .
               ", Kecepatan Maks: {$this->kecepatanMaks} km/jam";
    }

    public function klakson() {
        return "Beep! Beep!";
    }
}

// Child Class 2: Motor
class Motor extends Kendaraan {
    private $jenisMotor;
    private $kapasitasMesin;

    public function __construct($merk, $tahunProduksi, $warna, $kecepatanMaks, $jenisMotor, $kapasitasMesin) {
        parent::__construct($merk, $tahunProduksi, $warna, $kecepatanMaks);
        $this->jenisMotor = $jenisMotor;
        $this->kapasitasMesin = $kapasitasMesin;
    }

    public function getSpesifikasi() {
        return $this->getInfoDasar() . 
               ", Jenis: {$this->jenisMotor}" .
               ", Kapasitas Mesin: {$this->kapasitasMesin} cc" .
               ", Kecepatan Maks: {$this->kecepatanMaks} km/jam";
    }

    public function klakson() {
        return "Tinnn! Tinnn!";
    }
}

// Contoh penggunaan
$mobil1 = new Mobil("Toyota Avanza", 2022, "Silver", 180, 5, "Bensin");
$motor1 = new Motor("Honda Beat", 2023, "Merah", 110, "Bebek", 110);

// Menampilkan output
echo "<!DOCTYPE html>
<html>
<head>
    <title>UTS OOP - Ajeng Saufika</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        h1 { color: #2c3e50; }
        .output { background: #f9f9f9; padding: 15px; border-radius: 5px; margin-top: 20px; }
    </style>
</head>
<body>
    <h1>UTS OOP Presentasi - Ajeng Saufika</h1>
    <h2>Implementasi Class Parent dan 2 Child Class</h2>
    
    <div class='output'>
        <h3>Contoh Output:</h3>
        <p><strong>Mobil:</strong> {$mobil1->getSpesifikasi()}</p>
        <p>Suara klakson: {$mobil1->klakson()}</p>
        <p><strong>Motor:</strong> {$motor1->getSpesifikasi()}</p>
        <p>Suara klakson: {$motor1->klakson()}</p>
    </div>
</body>
</html>";
?>
