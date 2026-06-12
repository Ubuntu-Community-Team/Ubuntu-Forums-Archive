---
title: "Grub Help"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-05-15
Im trying to qued boot with grub but Fedora wont work When I click on it on the Grub menu instead it says "error 13: Invalid or unsupported expectable format" tryed a couple of things and places on /boot/grub/menu.lst and heres what it looks like "title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

title           Fedora
root            (hd0,1)
makeactive
chainloader     +1 

title           SuSE
root            (hd0,3)
makeactive  
chainloader     +1 

title           Fedora Linux 
root            (hdo,2)
makeactive      
chainloader     +1

title           Linux Fedora
root            (hd0,4)
makeactive
chainloader     +1

title           Fedora Linx
root            (hd0,0)
makeactive
chainloader     +1

title           blagh
root            (hd0,10)
makeactive
chainloader     +1
quiet

### END DEBIAN AUTOMAGIC KERNELS "
Fedoras on /dev/sda3 and ext3 is the file system.title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

title           Fedora
root            (hd0,1)
makeactive
chainloader     +1 

title           SuSE
root            (hd0,3)
makeactive  
chainloader     +1 

title           Fedora Linux 
root            (hdo,2)
makeactive      
chainloader     +1

title           Linux Fedora
root            (hd0,4)
makeactive
chainloader     +1

title           Fedora Linx
root            (hd0,0)
makeactive
chainloader     +1

title           blagh
root            (hd0,10)
makeactive
chainloader     +1
quiet

### END DEBIAN AUTOMAGIC KERNELS   
Fedoras on /dev/sda3 and file system is ext3 y ant it working is because fedora ant compatible or did i install it wrong or what? Lots of thanks for any help. And heres another thing thats on related but you might be able to help me with able

---

### Post by microsoft92sucks on 2007-05-15
srry dident mean to copy and paste that twice and heres where u could help me [http://ubuntuforums.org/showthread.php?t=443885](http://ubuntuforums.org/showthread.php?t=443885) 
I forgot to put it in srry again

---

### Post by annda on 2007-05-15
i'm not sure i know what you mean but this is definitely wrong

root (hdo,2)

you should have a 0 ZERO, not 'o' there.

---

### Post by microsoft92sucks on 2007-05-15
now im getting error 12

---

### Post by annda on 2007-05-15
> 12 : Invalid device requested.

make sure you have fedora on hda3 on sda3.

```
sudo fdisk -l
```

to find out what partitions host what systems. you seem to have more fedora partitions. was that intended or is your menu.lst wrong?

---

### Post by microsoft92sucks on 2007-05-15
justin@EggHead:~$ gksudo fdisk -l
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

theres the out put  im not sure what all of it means i only know a lil about this stuff

---

### Post by annda on 2007-05-15
it's not gksudo, it's plain sudo.

---

### Post by microsoft92sucks on 2007-05-15
srry 

justin@EggHead:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6474    52002373+  83  Linux
/dev/sda2            7726        9637    15358140   83  Linux
/dev/sda3            9638        9729      738990    5  Extended
/dev/sda4            6475        7725    10048657+  83  Linux
/dev/sda5            9638        9729      738958+  82  Linux swap / Solaris

---

