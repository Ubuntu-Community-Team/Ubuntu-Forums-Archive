---
title: "Como instalar el Token USB MS-IDProtect"
date: 2016-10-07
forum: Argentina Team
---

### Post by gmunioz on 2016-10-07
El Token USB MS-IDProtect, es el dispositivo usb, permite utilizar la firma digital implementada por el Poder Judicial de la Provincia de Buenos Aires en Argentina.
Para ello es necesario:

1- Obtener el middleware que debe ser provisto por el distribuidor del token, o descargarlo desde:
[http://www.aladdin-rd.ru/support/downloads/get?ID=39875](http://www.aladdin-rd.ru/support/downloads/get?ID=39875)
El archivo comprimido jacarta_pki_linux.zip, contiene versiones .deb y rpm. Para el caso de Ubuntu y derivados de Debian los archivos actuales son:

idprotectclient_637.03-0_amd64.deb -- 64 bits
e 
idprotectclient_637.03-0_i386.deb -- 32 bits
Estos archivos, una vez descomprimido el archivo jacarta_pki_linux.zip, se encuentran en el directorio /Deb

2- Instalar las dependencias requeridas, abriendo una terminal y ejecutando en ella:
exec sudo -i
apt-get update
apt-get dist-upgrade
apt-get install --reinstall coolkey gdebi libasedrive-usb libusb-1.0-0 libusb-1.0-0-dev libpcsclite-dev libpcslite1 libreadline6 libreadline6-dev libreadline-dev pcscd pcsc-tools opensc pinentry-gtk2 

3- Instalar mediante gdebi, el archivo correspondiente de 32 bits o 64 bits según nuestra distribución:
idprotectclient_637.03-0_amd64.deb -- 64 bits
ó
idprotectclient_637.03-0_i386.deb -- 32 bits

4- Reiniciar, apareceran en el escritorio los lanzadores para IDProtecT Manager e IDProtect PINTool y podrá ser reconocido y utilizado el token

Fuentes:
[http://www.proyectowww.com.ar/2016/05/notificacion-electronica-bs-as-asp](http://www.proyectowww.com.ar/2016/05/notificacion-electronica-bs-as-asp)...
[http://www.aladdin-rd.ru/support/](http://www.aladdin-rd.ru/support/)

---

