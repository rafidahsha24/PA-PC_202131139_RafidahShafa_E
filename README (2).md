
# DETEKSI BETUK GAMBAR MENGGUNAKAN CONTOUR

A. Teori yang mendukung projek 
1. **Baca dan Ubah Skema Warna Gambar**:
   Gambar awal dibaca menggunakan fungsi cv2.imread dari OpenCV. Gambar yang dibaca menggunakan skema warna BG (Blue-Green-Red) yang umum digunakan dalam OpenCV. 
 Namun, untuk menampilkan gambar menggunakan matplotlib, yang menggunakan skema warna RGB (Red-Green-Blue), skema warna gambar diubah menggunakan fungsi cv2.cvtColor dengan parameter cv2.COLOR_BGR2RGB.

2. **Citra Grayscale**:
Citra grayscale merupakan representasi dari gambar dalam skala abu-abu, yang hanya memiliki saluran warna tunggal. Dalam source code tersebut, gambar diubah menjadi citra grayscale menggunakan fungsi cv2.cvtColor dengan parameter cv2.COLOR_BGR2GRAY. Citra grayscale sering digunakan dalam berbagai operasi pengolahan gambar, seperti deteksi tepi dan pengenalan pola.

3. **Deteksi Tepian (Edge Detection)**:
Deteksi tepian adalah proses untuk mengidentifikasi perubahan yang signifikan dalam intensitas piksel di sekitar tepi objek dalam gambar. Dalam source code, tepian pada citra grayscale dideteksi menggunakan metode Canny dengan fungsi cv2.Canny. Metode Canny menggunakan algoritma yang menggabungkan deteksi tepi berdasarkan gradien intensitas dengan pemadatan tepi untuk menghasilkan tepian yang akurat.

4. **Mencari dan Menggambar Kontur**:
Setelah tepian terdeteksi, source code tersebut menggunakan fungsi cv2.findContours untuk mencari kontur pada citra tepian. Fungsi ini mengembalikan daftar kontur dan hierarki kontur. Kontur adalah garis kurva yang menghubungkan piksel-piksel yang memiliki intensitas serupa, sedangkan hierarki menggambarkan hubungan spasial antara kontur. Kemudian, kontur-kontur ini digambar pada gambar asli menggunakan fungsi cv2.drawContours dengan parameter yang sesuai.

5. **Menampilkan Gambar dan Plot**:
Source code menggunakan modul pyplot dari matplotlib untuk menampilkan gambar dan plot. Fungsi-fungsi seperti plt.subplot, plt.title, dan plt.imshow digunakan untuk membuat sub-plot, memberikan judul, dan menampilkan gambar pada sub-plot. Akhirnya, plt.show() digunakan untuk menampilkan tampilan plot lengkap dengan gambar-gambar yang telah dimasukkan ke dalam sub-plot.


B. Penjelasan Source code
1. Mengimpor library yang diperlukan:
    - import cv2: Mengimpor modul cv2 dari pustaka OpenCV, yang menyediakan berbagai fungsi untuk pengolahan gambar dan penglihatan komputer.
    - import numpy as np: Mengimpor modul numpy dan memberikan alias np.numpy adalah pustaka Python yang digunakan untuk melakukan operasi numerik dan manipulasi array.
    - from matplotlib import pyplot as plt: Mengimpor modul pyplot dari pustaka matplotlib, yang digunakan untuk membuat plot dan visualisasi data.
  
2. Membaca gambar:
image = cv2.imread('gambar.png'): Membaca gambar dengan nama file 'gambar.png' menggunakan fungsi imread dari pustaka OpenCV. Gambar tersebut disimpan dalam variabel image.

3. Mengubah skema warna gambar:
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB): Mengubah skema warna gambar dari BGR (Blue-Green-Red) menjadi RGB (Red-Green-Blue) 
menggunakan fungsi cvtColor dari OpenCV. Hal ini diperlukan karena matplotlib menggunakan skema warna RGB.

4. Membuat tampilan plot untuk gambar:
plt.figure(figsize=(10, 10)): Membuat objek plot dan menentukan ukuran tampilan plot.

5. Menampilkan gambar asli:
    - plt.subplot(2, 2, 1): Membuat sub-plot pada tampilan plot dengan ukuran 2x2, dan memilih sub-plot pertama.
    - plt.title("Original Image"): Memberikan judul pada sub-plot.
    - plt.imshow(image): Menampilkan gambar pada sub-plot.
    
6. Mengubah gambar menjadi citra grayscale:
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY): Mengubah gambar menjadi citra grayscale menggunakan fungsi cvtColor dari OpenCV.
    
7. Mencari tepian pada citra grayscale:
edged = cv2.Canny(gray, 30, 200): Menggunakan metode Canny untuk mendeteksi tepian pada citra grayscale. Parameter 30 dan 200 adalah batas bawah dan batas atas untuk deteksi tepian.
    
8. Menampilkan tepian pada citra:
    - plt.subplot(2, 2, 2): Memilih sub-plot kedua.
     - plt.title("Color Contours"): Memberikan judul pada sub-plot.
     - plt.imshow(edged): Menampilkan citra tepian pada sub-plot.
    9. Mencari kontur pada citra tepian:
       contours, hierarchy = cv2.findContours(edged, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE): Menggunakan fungsi findContours dari OpenCV untuk mencari kontur pada citra tepian. 
       Parameter cv2.RETR_EXTERNAL mengindikasikan hanya kontur eksternal yang akan ditemukan, dan cv2.CHAIN_APPROX_NONE mengindikas
