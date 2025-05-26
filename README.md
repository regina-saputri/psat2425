# Penilaian Sumatif Akhir Tahun
## Mapil DevOps XI TJKT 1 - Penilaian Praktek
### SMKN 1 Banyumas - TA. 2024 2025


#
# Cara mendeploy Aplikasi

# Nama Proyek

Deskripsi singkat mengenai proyek. Jelaskan secara ringkas apa yang dikerjakan aplikasi ini dan manfaatnya.

## Teknologi

- Amazon EC2 (Ubuntu Server)
- Nginx / Apache
- Node.js / Python / lainnya
- Git
- PM2 / Gunicorn / lainnya (opsional)

## Persiapan EC2

1. *Buat Instance EC2*
   - Gunakan Ubuntu Server (misalnya: Ubuntu 22.04 LTS).
   - Atur security group (buka port 22, 80, dan 443 jika perlu).

2. *Akses ke Instance*
  klik instance yang sudah kita buat tadi klik conect 


3. *Clone dan Deploy*
setelah dikonek tempel code berikut :
```
nano otomatis.sh 
#!/bin/bash
echo '#!/bin/bash
sudo apt update -y
sudo apt install -y apache2 php php-mysql libapache2-mod-php mysql-client
sudo rm -rf /var/www/html/{,.}
sudo git clone https://github.com/regina-saputri/psat2425 /var/www/html
sudo chmod -R 777 /var/www/html
echo DB_USER=admin > /var/www/html/.env
echo DB_PASS=P4ssw0rd  >> /var/www/html/.env
echo DB_NAME=rdsregina >> /var/www/html/.env
echo DB_HOST=rdsregina.c5lchhfugohi.us-east-1.rds.amazonaws.com >> /var/www/html/.env
sudo apt install -y openssl
sudo a2enmod ssl
sudo a2ensite default-ssl.conf
sudo systemctl reload apache2' > /home/ubuntu/otomatis.sh

chmod +x /home/ubuntu/otomatis.sh
```
## Langkah Terakhir
1. Salin ip public di halaman instance
2. Tempel ip public di browser
3. Jika halaman aplikasi psat2425 sudah muncul berarti sudah muncul.