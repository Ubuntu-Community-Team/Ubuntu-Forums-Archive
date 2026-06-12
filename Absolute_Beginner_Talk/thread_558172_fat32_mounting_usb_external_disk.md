---
title: "fat32 mounting usb external disk"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hacklab on 2007-09-23
i cant see mine disk,

what to do?
this is the the plot of ls -la /media :

roko@linux:~$ ls -la /media
total 68
drwxr-xr-x  7 root root  4096 2007-09-23 22:35 .
drwxr-xr-x 21 root root  4096 2007-09-23 18:40 ..
lrwxrwxrwx  1 root root     6 2007-09-23 18:28 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-09-23 18:28 cdrom0
lrwxrwxrwx  1 root root     7 2007-09-23 18:28 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-09-23 18:28 floppy0
-rw-r--r--  1 root root     0 2007-09-23 22:35 .hal-mtab
--wxr-x---  1 root root     0 2007-04-15 13:56 .hal-mtab-lock
drwxr-xr-x  2 roko roko  4096 2007-09-23 18:56 sdb1
drwxr-xr-x  2 roko roko  4096 2007-09-23 18:56 sdc1
drwxrwxrwx  1 root root 45056 2007-09-23 20:29 sdd1
roko@linux:~$

---

### Post by Pumalite on 2007-09-23
Post:

sudo fdisk -lu

---

### Post by hacklab on 2007-09-23
root@linux:~# sudo fdisk -lu

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157822559    78911248+  83  Linux
/dev/sda2       157822560   160826714     1502077+   5  Extended
/dev/sda5       157822623   160826714     1502046   82  Linux swap / Solaris

Disk /dev/sdd: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   321669494   160834716    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   781417664   390708801    c  W95 FAT32 (LBA)
root@linux:~#

---

### Post by Pumalite on 2007-09-23
sudo mkdir /media/sdc1
sudo mount -t /dev/sdc1 /media/sdc1

---

### Post by dmg412 on 2007-09-27
do you need sudo mount -t vfat /dev/sdc1 /media/sdc1

instead of 

sudo mount -t /dev/sdc1 /media/sdc1

I am not sure, just asking?

---

