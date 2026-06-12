---
title: "Help with Reading/Writing NTFS/FAT16 HDD's"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Fletcheri on 2006-11-09
Hey,

I've spent the last while reading through guides and posts and have only had a headache. I want to read/write (primarly read) to my other HDD's.
I have 1x 200gb SATA using "FAT16"
and 1 x 120gb SATA using "NTFS"

I'm booting from a 40gb IDE with linux set up on it.
My sudo fdisk -l looks like this:

> Disk /dev/sda: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200048565760 bytes
16 heads, 63 sectors/track, 387618 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      387618   195359440+   6  FAT16

Disk /dev/hdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4791    38483676   83  Linux
/dev/hdd2            4792        4998     1662727+   5  Extended
/dev/hdd5            4792        4998     1662696   82  Linux swap / Solaris


Any help would be much needed before i revert back to windows =/.

(Also I have already downloaded libntfs8 via synaptic and had no effect.)

Thanks

---

### Post by Ecthelion on 2006-11-09
The best HOWTO I know of for [writing to NTFS]("http://ubuntuforums.org/showthread.php?t=217009&highlight=howto+write+ntfs")

---

### Post by .t. on 2006-11-09
You should be able to write to fat easily. It's built in. Are the drives mounted? If not, you'll need to mount them "mount <device> <mountpoint>" and try using them.

---

### Post by Fletcheri on 2006-11-09
> **.t. said:**
> You should be able to write to fat easily. It's built in. Are the drives mounted? If not, you'll need to mount them "mount <device> <mountpoint>" and try using them.

When i right click and select mount, or double click their icons i get an "unable to mount" error:

error: device /dev/sdb1 is not removable

error: could not execute pmount

i tried  "mount /dev/sdb1  disk1" and "mount /dev/sdb1 /desktop"
but had no luck, not sure exactley how to mount manually fomr what you said either.  Sorry, still no luck.

---

### Post by bodhi.zazen on 2006-11-09
> **Fletcheri said:**
> When i right click and select mount, or double click their icons i get an "unable to mount" error:

error: device /dev/sdb1 is not removable

error: could not execute pmount

i tried  "mount /dev/sdb1  disk1" and "mount /dev/sdb1 /desktop"
but had no luck, not sure exactley how to mount manually fomr what you said either.  Sorry, still no luck.

For /dev/sdb1:

```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1 -o umask=000
```
You can change the name of the mount point to what you want.

Add an entry to fstab:> /dev/sdb1 /mnt/sdb1 auto users,umask=000 0 0

For your NTFS, follow the above link, then similar steps to mount the partition.

---

