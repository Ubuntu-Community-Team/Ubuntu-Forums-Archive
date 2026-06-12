---
title: "memòria USB muntada en dos llocs"
date: 2009-06-24
forum: Catalan Team
---

### Post by indiosincracia on 2009-06-24
Hola tinc un flaix de memoria USB que s'hem munta en dos llocs diferents  /dev/sdb i /dev/sdc, com ho he de fer per que es munti en un sol lloc quan l'endollo.
merci.
target@blank:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e88b61a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 502 MB, 502792192 bytes
16 heads, 60 sectors/track, 1022 cylinders
Units = cylinders of 960 * 512 = 491520 bytes
Disk identifier: 0xc4311667

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
target@blank:~$

---

### Post by torracastanyes on 2009-06-24
Tens dues particions dintre de la memòria?

Per la taula que has posat sembla que sí.  Quant jo connecto una memòria amb més d'una partició, sempre me les munta per separat, pot ser?

---

### Post by indiosincracia on 2009-06-24
Podria ser, ja no recordo que vaig fer, pero com es fa per ajuntar-les, al qtparted hem surten per separat:
Disks
 /dev/sda
 /dev/sdb
 /dev/sdc

---

### Post by oriolsbd on 2009-06-24
Hola.

Ull, el /dev/sda no és un USB, sinó el teu disc dur. Per ajuntar la /dev/sdb i la /dev/sdc (si realment són dues particions del mateix USB, que sembla ser que sí) hauries d'eliminar la partició /dev/sdc i després ampliar la /dev/sdb perquè agafi l'espai alliberat per l'altra. Abans de fer-ho, per si de cas, fes còpia de seguretat del que tinguis a /dev/sdc (no serà molt, perquè només té 1Mb). En aquest cas, una bona idea, tenint en compte que es tracta d'una partició tan petita, és fer un volcat d'aquesta, en comptes de copiar el que hi hagi a la partició:
```
sudo dd if=/dev/sdc of=/home/el_teu_usuari/sdc.img
```

Salut!

---

### Post by indiosincracia on 2009-06-24
No pateixis no hi ha res,
target@blank:~$ sudo fdisk /dev/sdc

Command (m for help): d
No partition is defined yet!

target@blank:~$ sudo fdisk /dev/sdb

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sdb: 502 MB, 502792192 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4311667

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

continuen apareixent totes dos, /dev/sda és el meu disc dur.

---

### Post by akyra on 2009-06-26
Ho has probat amb el GParted?

---

### Post by indiosincracia on 2009-06-26
Si també, el resultat és igual que amb el qtparted

---

### Post by PatrickVogeli on 2009-06-27
jo diria que no son particions, sino dues memories per separat. Si fossin dues particions serien sdb1 i sdb2. Una es la memoria principal que vas comprar i l'altra, diria que potser hi anava algun programa criptografic o manual d'instruccions o alguna xorrada aixi.

salut

---

### Post by indiosincracia on 2009-06-29
Si, he fet particions i sut sdX1, sdX2, sdX3 etc...
semblen dos memòries per separat, però mai me'n havien sortit dos, total, amb aquesta calor s'ha degut podrir per dins...:-?

---

