---
title: "d drive"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by mindworm on 2006-10-16
i have a d drive that i think is formatted with ntfs and i'm wondering how i could access the files on it

i don't know what information to give, but i can probably answer questions if anyone needs to know something to help me

thanks=/

---

### Post by ReaderRat on 2006-10-16
> **mindworm said:**
> i have a d drive that i think is formatted with ntfs and i'm wondering how i could access the files on it

i don't know what information to give, but i can probably answer questions if anyone needs to know something to help me

thanks=/
Run this in Terminal & post the results:
```
cat /etc/fstab
```

---

### Post by mindworm on 2006-10-16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ReaderRat on 2006-10-16
Please post:
```
fdisk -l
``` That is an L, not a one

---

### Post by mindworm on 2006-10-16
is that a command to run?

---

### Post by ReaderRat on 2006-10-16
Yes

---

### Post by mindworm on 2006-10-16
did it

what's it supposed to do, and then how do i get to the d drive?

---

### Post by ReaderRat on 2006-10-16
Sorry if I did not make myself clear. Please run in Terminal:
```
fdisk -l
```
And post the output here for us to look at.

---

### Post by mindworm on 2006-10-16
i see no output when i put that command in

---

### Post by ReaderRat on 2006-10-16
Try
```
sudo fdisk -l
```
Sorry, I goofed.

---

### Post by mindworm on 2006-10-16
there we go

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Extended
/dev/sda5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    c  W95 FAT32 (LBA)

---

### Post by ReaderRat on 2006-10-16
I don't know what the partition **sda2** is, no info in fstab or fdisk to tell how it's formatted. This post will bump you back to first. Maybe someone more knowledgeable can help.

---

### Post by Iowan on 2006-10-16
Looks kinda/sorta like mine - except I have hda1/2/5 (and no second drive).
It looks unusual to the untrained (my) eye - but notice the block start/stop is the same for sda2 as sda5 - the swap partition.
If sdb is supposed to be D:, it appears (to the same untrained eye) to be FAT32 instead of NTFS.

---

### Post by confused57 on 2006-10-16
Maybe you could mount the "d" drive, using this tutorial:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Looks like it's partitioned FAT32.

---

