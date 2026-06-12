---
title: "2 fast questions"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by kiwiz on 2006-07-15
Hi, i got 2 questions:P

1. How do i change language? dont want swedish anymore :p
2. How do i accses my fat32 partiton?

---

### Post by GuitarHero on 2006-07-15
1.  its in administration or settings or something, a flag icon.
2.  mount it

---

### Post by kiwiz on 2006-07-15
well how do i mount it? when i try to accses it, it says "Unable to mount the selected volume." "Error: device /dev/sda9 is not removable" "Error: could not execute pmount"

---

### Post by skale on 2006-07-15
What is the partition called? (as in /dev/hda1)

type sudo mount -a
if that doesn't work try sudo mount [name of partition]


If neither work, post whatever error messages seen and the contents of the /etc/fstab file.

---

### Post by kiwiz on 2006-07-15
when i typ sudo mount -a nothing happends.
The way i tried to moint it was simply to right click on it and press "mount volume" and that is when i get the error msg i wrote above.

---

### Post by skale on 2006-07-15
type **cat /etc/fstab**
and post the output

---

### Post by kiwiz on 2006-07-15
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /boot           ext3    defaults        0       2
/dev/sda8       /home           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by kiwiz on 2006-07-15
anyone? =(

---

### Post by skale on 2006-07-15
It's not on the list, wierd...

Can't think what it is. It should be on the list.

---

### Post by kiwiz on 2006-07-15
=(

---

### Post by Drakkor on 2006-07-15
Huh? I don't know why /dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda would be your optical drive? Mine is:
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /windows2 ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /windows3 vfat iocharset=utf8,umask=000 0 0 
/dev/hda7 /windows4 ntfs nls=utf8,umask=0222 0 0

---

### Post by drtvasudevan on 2006-07-15
at the time of installation fat32 was not added to the fstab.
now you have to edit fstab manually and try to mount.

---

