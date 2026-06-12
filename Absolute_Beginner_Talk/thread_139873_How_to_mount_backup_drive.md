---
title: "How to mount backup drive"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by dicecca112 on 2006-03-05
If someone could help me it would be great I tried this

[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

and it said that the mount point doesn't exist

here is my fdisk the drive I want to mount is sdb1, it has all my music on it, and I would kinda like to listen to it.  

> Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631    7  HPFS/NTFS
/dev/sda2   *        5006        9804    38547967+  83  Linux
/dev/sda3            9805       10011     1662727+   5  Extended
/dev/sda5            9805       10011     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         992      999813+   6  FAT16


---

### Post by jimrz on 2006-03-05
Try ***[COLOR="Sienna"][[COLOR="Sienna"]this[/COLOR]]("http://www.ubuntuguide.org/#automountntfs")[/COLOR]*** one. It worked nicely for me. Be sure to scroll down the page to the part that shows how you amke it auto-mount each time you spin'er up.

---

### Post by dicecca112 on 2006-03-05
thanks that worked perfectly

---

