---
title: "posició partició swap"
date: 2010-06-29
forum: Catalan Team
---

### Post by abosch on 2010-06-29
L'altre dia cercant informació, vaig llegir que és millor tenir la partició intercanvi (swap) al final. Les vegades que he instal.lat ubuntu, fins ara no ho tenia en compte. 

Trec algunes de les ordres que em sembla aporten informació,  

> 
abosch@abb-ntbk:~$ sudo fdisk -l

Disc /dev/sda: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a7e27f0

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2554      979965   82  Intercanvi Linux / Solaris
/dev/sda3            2555       30401   223681027+  83  Linux

abosch@abb-ntbk:~$ df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda1              19G  2,9G   15G  17% /
udev                  973M  268K  973M   1% /dev
none                  973M  232K  973M   1% /dev/shm
none                  973M  100K  973M   1% /var/run
none                  973M     0  973M   0% /var/lock
none                  973M     0  973M   0% /lib/init/rw
/dev/sda3             210G   40G  160G  20% /home

abosch@abb-ntbk:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ba42b8f1-cdb1-4305-a7d6-354d2c12ad2d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=ed2456c3-1657-46de-a86b-d3742f11ffdb /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=d96e6f38-7422-4e5a-9a3f-3cb3d8de7415 none            swap    sw              0       0
abosch@abb-ntbk:~$ 



Hi ha algun problema en continuar així? 

gràcies

---

