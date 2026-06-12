---
title: "[SOLVED] Grub Sin Windows"
date: 2007-10-21
forum: Argentina Team
---

### Post by Timbis on 2007-10-21
No puedo iniciar guindous luego de instalar ubuntu 7.10, configure el grub pero no funca :

title		Windows Xp
root		(hd0,4)
makeactive

chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ca8f887f-e917-41b4-8f22-3963f7fa4daa ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

y asi es mi disco particionado:

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda2               1        9733    78180291    f  W95 Ext'd (LBA)
/dev/hda5            6376        9733    26973103+   b  W95 FAT32
/dev/hda6   *           1        3649    29310498   83  Linux
/dev/hda7            3650        6375    21896563+   b  W95 FAT32

el guindous esta en la particion hda5, Gutsy si inicia.
ya probe con todos los (hd?,?) que puede aver (los cambie en el entorno del grub)

Tambien use el super grub disk, pero no funco tampoco.



gracias de antemano, es con algo de urgencia. Toy a su dispocicion si necesitan mas info.

---

### Post by Hernán-Amaya on 2007-10-21
me parece que windows tiene que estar instalado en el primer disco por eso no te bootea

---

### Post by Timbis on 2007-10-21
Help!!

---

### Post by margori on 2007-10-21
Hola Timbis. Esoty viendo tu problema pero me falta un poco de informacion:

No comprendo si antes de instalar Ubuntu tenias instalado XP, este estaba instalado en una unidad logica (hda5 en este caso), ya que normalmente en una instalacion limpia de windows este crea una particion primaria activa y se instala todo ahi, las demas son todas particiones extendidas.

La pregunta es, te funciono windows antes de instalar Ubuntu?

Por otro lado, que error de tira windows?

---

### Post by Timbis on 2007-10-22
Al final era el maldito guindous, ya tenia xp y vista (original) de antes,  desinstale vista y la mugre se llevo todos los archivos de booteo. 
Gracias a todos los que preocuparon...

---

