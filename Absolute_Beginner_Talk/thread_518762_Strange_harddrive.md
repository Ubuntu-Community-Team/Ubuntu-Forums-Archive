---
title: "Strange harddrive"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Geir102 on 2007-08-06
Hello!
Hi i have a problem whit my ntfs partition, it worked fine but when it got full i started to delete stuff but there is no space freed. And it dosent show up when i use XP anymore any one know what I am doing wrong?

---

### Post by asmoore82 on 2007-08-06
did you load the ntfs3 driver to enable write support?

---

### Post by Geir102 on 2007-08-06
Yes the stuff gets deletet but it just dosent free up space. I use ntfs-config

---

### Post by asmoore82 on 2007-08-06
are you deleting it via a GUI?
if yes, then is it going to your trash?

---

### Post by Geir102 on 2007-08-06
Yes i use GUI, but i have emtyd the trase on the dekstop, if there is any other plase please tell my.

---

### Post by ThrobbingBrain66 on 2007-08-06
I don't have any external drives, but I believe whenever a drive is mounted in Ubuntu, it puts a .Trash folder actually on the drive.  You have to clean that one out as well.  Since it's a hidden folder, you'll have to hit ctrl+h to see it.

---

### Post by Geir102 on 2007-08-06
you are a genius tanks a lot:-D

---

### Post by alienexplorers on 2007-08-06
Can you list here the output of sudo fdisk -l.

---

### Post by Geir102 on 2007-08-06
Disk /dev/sda: 20.4 GB, 20418772480 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1971    15832026    7  HPFS/NTFS
/dev/sda2            1972        2002      249007+  82  Linux swap / Solaris
/dev/sda3            2003        2482     3855600   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

---

