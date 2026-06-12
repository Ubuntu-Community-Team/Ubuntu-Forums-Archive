---
title: "Fallò el inicio de sesòn con disco encriptado"
date: 2015-03-28
forum: Argentina Team
---

### Post by federico.schaerer on 2015-03-28
Amigos, buenas. Tengo un gran problema con ubuntu 14.04: al instalarlo marque la opciòn de encriptaciòn de disco. Ahora cuando quiero entrar me pide la clave de encriptaciòn y paso a la clave paraentrar a la computadora, me pide la clave y me dice: fallò el inicio de sisiòn, tanto de mi usuario como de invitado. Tengo archivos muy importantes que no puedo perder. Home no està en una particiòn separada, està todo junto.
Gracias por la ayuda.

---

### Post by gmunioz on 2015-04-02
Inicia con un Live-Usb/Dvd de Ubuntu 14.04 de la misma versión (32 ó 64 bits)
Localiza la partición del disco rígido, abre una terminal y ejecuta en ella:
> sudo -i
fdisk -l
Su pongamos sea /dev/sda1
Monta la partición cifrada y busca el directorio de cifrado, ejecutando en la terminal:
> mount /dev/sda1 /mnt
cd /mnt
ecryptfs-recover-private
Si encuentra un directorio cifrado, te preguntara si deseas recuperarlo, responde "y" o "s".
Te preguntara la contraseña o passphrase, escríbela.
Si todo sale bien, tu directorio se montara automáticamente, toma nota de la ruta de montaje y recupera los archivos.

---

