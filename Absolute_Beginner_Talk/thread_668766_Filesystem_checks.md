---
title: "Filesystem checks"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by liquidus219 on 2008-01-15
Hi, I have an Acer 5600 series laptop, 120GB HD, Win XP with Gutsy Gibbon on an extended partition.

Ubuntu boots up properly, but every time, it takes around five minutes just to check the filesystems on each partition - below is the layout of my system:

Partition 1 - PQSERVICE (Acer recovery)
Partition 2 - Win XP
Extended Partition - 30GB Free space (Partition 3), 1GB swap space (Partition 4), Ubuntu (Partition 5)

Is it supposed to take so long, or is that just because it's on an extended partition?

---

### Post by yabbadabbadont on 2008-01-15
It is most likely spending most of that time checking the WinXP partition.  If you like, I can show you how to prevent it from checking the XP partition on every boot.  Just post the contents of your /etc/fstab file.  You only have to change one character in it.  :)

---

### Post by liquidus219 on 2008-01-15
Here's the contents of that file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a2a9affa-a1de-4aa9-adf9-8d36bef47f6d /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=16D9-B5D2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C32-840D  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=B8A9-D770  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1613f85a-7f4e-437d-be03-5455df4ec73f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


which character do I need to change?

---

### Post by yabbadabbadont on 2008-01-15
It looks like you actually have three fat32 partitions (vfat).  Did you forget to list one of them?  Anyway, just change the "1" to a "0" (zero) on the three lines with vfat.  i.e.  /media/sda1, /media/sda2, and /media/sda3.

---

### Post by liquidus219 on 2008-01-15
Thanks, it works perfectly now - sorry about the extra partitions, I had one extra one so I could share files between OS's.

---

### Post by yabbadabbadont on 2008-01-15
No problem, glad it worked for you.  Just remember to check the fat32 filesystems once in a while when you are booted into XP.

---

