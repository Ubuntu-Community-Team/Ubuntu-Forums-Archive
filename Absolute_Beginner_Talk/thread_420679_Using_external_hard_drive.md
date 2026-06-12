---
title: "Using external hard drive"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Tintinnabulation on 2007-04-23
I just got an iomega external hard drive and formatted it to ntfs.
I want to use this in feisty, i.e. have read/write access.
So i think i need to somehow mount it then install ntfs-3g.

Problem is i don't know how to mount it or get access to it.  In general, I know little about this kind of thing.   (NOW FIXED)
Any help would be greatly appreciated.   

Here is fdisk if that helps at all.

```
user@user-laptop:~$ sudo fdisk -l
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6380    51199155    7  HPFS/NTFS
/dev/sda3            9154        9545     3148740   db  CP/M / CTOS / ...
/dev/sda4            6381        9153    22274122+   5  Extended
/dev/sda5            6381        7655    10241406   83  Linux
/dev/sda6            7656        9057    11261533+  83  Linux
/dev/sda7            9058        9153      771088+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```

---

### Post by Happy_Man on 2007-04-23
Well, it already seems to be mounted; do you mean that it is not showing up in Nautilus?

---

### Post by Tintinnabulation on 2007-04-23
Oh ok, then.
Yes, I can't find it in nautilus - i checked under media/

---

### Post by Tintinnabulation on 2007-04-23
Wait - I'm an idiot. 
I rebooted for a second time and this time it come up on the desktop.
It also showed some stuff stored on it that windows didn't show, oddly enough.

Thanks for you time

---

