---
title: "Reinstal·lar Windows sense perjudicar Ubuntu"
date: 2010-10-08
forum: Catalan Team
---

### Post by jmfubu on 2010-10-08
Tinc Ubuntu 10.04 en un disc dur (sda)  i Windows en un altre disc dur amb dues particions, una amb dades (sdc2) dades i una altra amb sistema (sdc1). He de reinstal·lar Windows però em demana escriure arxius d'inici en el disc sda on, és clar, no troba partició adequada. Sembla que tal com ho tinc no pugui instal·lar Windows sense perjudicar Ubuntu.  Encara tinc un tercer disc dur (sdb) utilitzable.

Què puc fer? 

Gràcies. 
Disc /dev/sda: 40.0 GB, 40020664320 octets
255 heads, 63 sectors/track, 4865 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d922c

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Estesa
/dev/sda5            4661        4866     1648640   82  Intercanvi Linux / Solaris

Disc /dev/sdb: 120.0 GB, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8491e5f

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1               1       14592   117210208+   7  HPFS/NTFS

Disc /dev/sdc: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06520651

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdc2            5100       60801   447426315    7  HPFS/NTFS

---

### Post by wgarcia on 2010-10-09
Windows vol escriure als registres d'arrencada de tots els discos, sense prendre en compte si hi ha altres sistemes operatius (al contrari de les distribucions de linux que respecten el que troben) i per tant penso que no hi ha manera que respecti el teu disc sda (política de monopoli...). 

Per tant se m'acudeixen dues opcions:

1) desconnectar el disc "sda" i després tornar-lo a connectar i des d'ubuntu fer "update-grub", tot i que suposo que no faria falta. 

2) fer la reparació i després des d'un Live CD reparar el grub que s'haurà carregat el Windows, en la línia del que se suggereix aquí:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jmfubu on 2010-10-11
Gràcies. 

He fet el sistema de desconnectar el disc.
Ubuntu s'ha engegat perfecte. I per engegar Windows només ha calgut fer update-grub. Abans de fer-ho sortia el missatge "Falta NTLDR".

Moltes gràcies.

---

### Post by wgarcia on 2010-10-12
Perfecte.

El [Solved]  l'has de posar amb el menú "Thread Tools" que tens a dalt.

---

