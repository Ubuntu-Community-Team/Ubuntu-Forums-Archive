---
title: "problems mounting ntfs partition, ntfs-config installed"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by LiterallyDude on 2007-07-05
hi. i'm using kubuntu feisty and i'm having problems mounting my ntfs partition. Here is the fdisk output:

> Disk /dev/sda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6079    48829536   83  Linux
/dev/sdb2            6080       24321   146528865    5  Extended
/dev/sdb5            6080       24072   144528741   83  Linux
/dev/sdb6           24073       24321     2000061   82  Linux swap / Solaris

I have ntfs-3g and ntfs-config installed. When I open ntfs-config, it doesn't give my an option to enable write support for an internal drive (only an external).

i can kdesu konqueror and see the files, but i can't copy, write, etc..

what should i try next?

---

### Post by Nythain on 2007-07-05
edit your fstab to have it mount with the nfts-3g driver and edit the ownership

---

### Post by LiterallyDude on 2007-07-05
no dice. here is my fstab

> proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=aa348546-0fce-4e14-afae-8ae4d257b309 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/sdb5 :
UUID=62d8c763-6f61-409f-a2f3-654d8acf8bd3 /home/ed ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# Entry for /dev/sdb6 :
UUID=084da676-5efd-4e33-8546-cd13540edc3b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /home/bak auto user,atime,auto,rw,dev,exec,suid 0 0

what to try next?

---

### Post by LiterallyDude on 2007-07-05
i got it. it wasn't clear on how i had to edit my fstab. 

i changed:

/dev/sda1 /home/bak auto user,atime,auto,rw,dev,exec,suid 0 0

to:

/dev/sda1 /home/bak ntfs-3g defaults,locale=en_US.utf8 0 0

and everything looks good now.

---

