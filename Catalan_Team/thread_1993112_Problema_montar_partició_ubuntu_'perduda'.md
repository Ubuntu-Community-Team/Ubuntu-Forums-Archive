---
title: "Problema montar partició ubuntu 'perduda'"
date: 2012-06-01
forum: Catalan Team
---

### Post by pserra on 2012-06-01
Hola,
després de molt de temps sense problemes en ubuntu... l'altre dia al netbook em va fallar la veu.... i després al reiniciar ja vaig perdre el grub.
Si engego des de el Supergrub en troba les particions 'finestres', però l'arrel de ubuntu no me la troba. Crec recordar que vaig instal·lar l'arrel a sda6 i la home a sda7.

Des de la live cd també tinc problemes al montar:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37c0b349

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8388608    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1045        4293    26093890+   7  HPFS/NTFS
/dev/sda3            4294        5075     6281415    7  HPFS/NTFS
/dev/sda4            5076       19457   115523415    f  W95 Ext'd (LBA)
/dev/sda5            5076       17545   100165243+   b  W95 FAT32
/dev/sda6           17546       18274     5855661   83  Linux
/dev/sda7           18275       19086     6522358+  83  Linux
/dev/sda8           19087       19457     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 
gparted:
[IMG]http://img137.imageshack.us/img137/263/gparted.png//[/IMG]
[IMG]http://imageshack.us/photo/my-images/137/gparted.png/[/IMG]
[[IMG]http://img137.imageshack.us/img137/263/gparted.png[/IMG]](http://imageshack.us/photo/my-images/137/gparted.png/)

---

### Post by CarlesOriol on 2012-06-02
Pots ser que la versió insta&#320;lada fos més moderna que la que estas executant i la teva home tingui un sistema d'arxius btrfs o un altre no suportat per la live que uses?

---

### Post by pserra on 2012-06-02
Merci Carles Oriol,
a veure si demà ho puc probar amb un altre live.... ja comentaré com em va.... 
Merci.

---

### Post by pserra on 2012-06-04
Hola,
acabo de provar-ho amb el live cd que al seu dia vaig instal·lar-ho(koala remix 9.10 )i em fa el mateix:
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: you must specify the filesystem type


alguna altre idea?
Merci

---

### Post by pserra on 2012-06-06
Gràcies per l'ajuda...
davant dels problemes que tinc de montar la partició  i com que tinc l'arrel separada de la home, he tornat a instal·lar el ubuntu a la versió  que m'ha anat millor.
Gràcies.

---

