---
title: "Gparted help"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by KnoTHavok on 2006-10-27
When i use gparted in 6.10 it doesn't recognize the partitions of my hard drive all it says is unallocated space.
I did fdisk -l and i showed my partitions but gparted wont.
```
======================
libparted : 1.7.1
automounting disabled
======================
Can't have overlapping partitions.

```
That is what i get when i start it from the terminal

Here is the fdisk printout
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4982    40017883+   7  HPFS/NTFS
/dev/hdc2            4983        9729    38130277+   5  Extended
/dev/hdc3            9453        9729     2224971   82  Linux swap / Solaris
/dev/hdc5            4983        6806    14651217   83  Linux
/dev/hdc6            6807        9452    21253963+   7  HPFS/NTFS

```

---

