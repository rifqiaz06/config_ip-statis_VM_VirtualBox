Untuk mengatur IP statis pada mesin virtual (VM) di VirtualBox, Anda perlu melakukan beberapa langkah konfigurasi pada VirtualBox dan pada sistem operasi tamu (VM) itu sendiri. 

# Langkah-langkah:
## 1. Konfigurasi Adapter Jaringan di VirtualBox:
- Matikan VM yang ingin dikonfigurasi.
- Pilih VM tersebut, lalu klik "Settings" (Pengaturan).
- Buka tab "Network" (Jaringan).
- Pada Adapter 1, pastikan terhubung dengan "NAT" untuk akses internet.
- Tambahkan Adapter 2 dengan memilih "Host-only Adapter" (Adaptor Khusus Host) pada "Attached to".
- Pilih nama jaringan khusus host yang sesuai, misalnya "vboxnet0". 
- Klik "OK" untuk menyimpan pengaturan.

## 2. Konfigurasi IP Statis pada Sistem Operasi Tamu:
### - Linux (misalnya, Debian):
- Buka terminal pada VM.
- Edit file konfigurasi jaringan, misalnya `/etc/network/interfaces` atau `/etc/netplan/*.yaml`.
- Ubah konfigurasi untuk antarmuka jaringan yang terhubung ke "Host-only Adapter" (biasanya `enp0s8` atau yang serupa).
- Gunakan alamat IP yang sesuai dengan jaringan Host-only, misalnya `10.10.10.11`, dan subnet mask `255.255.255.0`.
- Simpan perubahan dan restart layanan jaringan (misalnya, `sudo systemctl restart networking` atau `sudo netplan apply`). 

### - Windows:
- Buka "Network and Sharing Center" (Pusat Jaringan dan Berbagi).
- Klik "Change adapter settings" (Ubah pengaturan adaptor).
- Klik kanan pada adaptor jaringan yang terhubung ke jaringan Host-only dan pilih "Properties" (Properti).
- Pilih "Internet Protocol Version 4 (TCP/IPv4)" dan klik "Properties".
- Pilih "Use the following IP address" (Gunakan alamat IP berikut) dan masukkan alamat IP statis, subnet mask, dan gateway default yang sesuai dengan jaringan Host-only.
- Klik "OK" untuk menyimpan pengaturan. 

<img width="658" height="427" alt="Screenshot 2025-07-22 213941" src="https://github.com/user-attachments/assets/6df3ad58-7de5-422f-87ef-a0e2306818e2" />

<img width="655" height="424" alt="Screenshot 2025-07-22 214733" src="https://github.com/user-attachments/assets/c43da110-ba5c-4a9d-a016-1ac7c0c5d0ee" />

<img width="400" height="298" alt="Screenshot 2025-07-22 215127" src="https://github.com/user-attachments/assets/abdb61eb-c112-4136-a5f2-65598ec63f47" />

## 3. Uji Koneksi:
- Setelah konfigurasi selesai, hidupkan VM.
- Lakukan ping dari VM ke host dan sebaliknya untuk memastikan koneksi berhasil.

## Catatan Penting:
- Pastikan alamat IP yang Anda pilih untuk VM tidak bertabrakan dengan alamat IP lain di jaringan. 
- Alamat IP, subnet mask, dan gateway default harus sesuai dengan pengaturan jaringan Host-only di VirtualBox. 
- Beberapa sistem operasi mungkin menggunakan alat atau cara konfigurasi yang berbeda, jadi pastikan untuk merujuk pada dokumentasi sistem operasi yang Anda gunakan.

Dengan mengikuti langkah-langkah di atas, Anda dapat berhasil mengatur IP statis pada mesin virtual di VirtualBox.
