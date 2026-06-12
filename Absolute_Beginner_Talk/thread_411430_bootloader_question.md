---
title: "bootloader question"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-04-16
Can someone give me the correct entries for me to boot partition /dev/sdb1 (The highlighted one) which is on an IDE drive. Grub is on the SATA drive.

[COLOR=DarkGreen]localhost tony # fdisk -l

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2459    19751886    7  HPFS/NTFS
/dev/sda2            2460        2472      104422+  83  Linux
/dev/sda3   *        2473       10000    60468660   83  Linux
/dev/sda4           10001       38913   232243672+   5  Extended
/dev/sda5           10001       19999    80316936   83  Linux
/dev/sda6           20001       38913   151918641   83  Linux

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[/COLOR][COLOR=DarkGreen]**/dev/sdb1   *        8710        9729     8193150   83  Linux**
/dev/sdb4               1        8709    69955011    5  Extended
/dev/sdb5               1        3310    26587512   83  Linux
/dev/sdb6            3311        8661    42981876    b  W95 FAT32
/dev/sdb7            8662        8709      385528+  82  Linux swap / Solaris

Partition table entries are not in disk order[/COLOR]


I have tried

rootnoverify (hd1,0)
chainloader +1


and is gives me a GRUB error 13


thanks, tchoklat

---

### Post by chakkaradeep on 2007-04-16
> **tchoklat said:**
> 
I have tried

rootnoverify (hd1,0)
chainloader +1


When you type the command,

*rootnoverify (hd* and press tab, it will show the possible options and then after hd1 (if it is), again press tab, it will show available options :) 

And moreover, the Grub Error 13 is,

*This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).*

So i also doubt there is some problem with ur kernel

---

