---
title: "mounting partitions"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-10-20
I'm trying to mount two partitions and have the drive icons show up on the desktop. I've done it before and had it work but now I'm getting error messages (mount point 0 does not exist).

This is the result of fdisk -l:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096   83  Linux
/dev/sda2            6528        6853     2618595   82  Linux swap / Solaris
/dev/sda3            6854       13380    52428127+  83  Linux
/dev/sda4           13381       20023    53359897+   b  W95 FAT32


I'd like to mount sda3 and sda4. The mount point for sda3 is /mnt/Ext3 and for sda4 it is mnt/FAT32. What do I need to add to the fstab file?

---

### Post by taurus on 2006-10-20
If you want those two partitions to appear on your desktop, you need to mount them to /media...

```

sudo mkdir /media/EXT3 /media/FAT32

```
Then, edit your /etc/fstab, "gksudo gedit /etc/fstab", and include these two lines...

```

/dev/sda3  /media/EXT3  ext3  defaults  0  1
/dev/sda4  /media/FAT32  vfat   defaults,umask=0000  0  0

```
Reboot...

---

### Post by ReaderRat on 2006-10-20
This may help:
[**Mount Ubuntu Partition**](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by beamo on 2006-10-20
Thanks, taurus. Works great! :-D 

You too, ReaderRat.

---

