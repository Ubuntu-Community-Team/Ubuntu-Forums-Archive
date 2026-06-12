---
title: "Iniciar Windows XP con NTFS desde Grub"
date: 2008-02-02
forum: Argentina Team
---

### Post by melvinlopez06 on 2008-02-02
hola, buenas :D
Tengo un problem con windows -raro- y grub.
Por desgracia del destino en la universidad nos hacen ocupar windows, asì que desempolve un disco duro de 30 Gb donde estaba windows, y en uno de 40 que tengo mi ubuntu.

El problema es que quiero agregar la entrada para el cargador de windows en grub, hasta donde mis conocimientos llegan (segun yo) era necesario colocar solo esto.

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

------------
raiz ubuntu en hda1 (ext3)
raiz windows en hdb1 (ntfs)

Al iniciar el grub aparece la entrada de win, y al intentar cargarla solo dice "Unknow partition type" y no la arranca.

El disco duro de win esta como esclavo y el de ubuntu como maestro.
Les dejo las entradas del menu de grub
---------------------

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e2009016-2059-42d0-9a86-1f8064eb673e ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e2009016-2059-42d0-9a86-1f8064eb673e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e2009016-2059-42d0-9a86-1f8064eb673e ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e2009016-2059-42d0-9a86-1f8064eb673e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

-------------
saludos ! :D

---

### Post by Hei Ku on 2008-02-02
tenes conectado ademas un cdrom ide? eso podria cambiar el numero correspondiente al xp

---

### Post by melvinlopez06 on 2008-02-02
hola Hei Ku, pues fijate que si tengo conectado un quemador de dvd, pero con la cincha secundaria.

Es decir los discos duros estan juntos, y quemador aparte.
Aunque no se me habia ocurrido eso !
Probare cambiar un par de cosas y luego posteo.

---

