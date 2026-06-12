---
title: "Can I copy my Ubuntu installation to another drive?"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-11-14
I had Ubuntu installed in a slow hard drive temporarily and now I need to put ubuntu and swap to a fast drive. What is the best way to do this? Copy everything to another drive or install from scratch?

---

### Post by Darrin on 2005-11-14
[This thread]("http://www.ubuntuforums.org/showthread.php?t=80389") might have some answers for you.

---

### Post by cafevincent on 2005-11-14
[QUOTE=Darrin][This thread]("http://www.ubuntuforums.org/showthread.php?t=80389") might have some answers for you.[/QUOTE]

This may not be the right thing for me, the size of my ubuntu drive is 233GB and the target drive is only 37gb. As I understand it cloning requires the target partition to be the same size as the original.

---

### Post by GTvulse on 2005-11-14
[QUOTE=cafevincent]This may not be the right thing for me, the size of my ubuntu drive is 233GB and the target drive is only 37gb. As I understand it cloning requires the target partition to be the same size as the original.[/QUOTE]
Use rsync. I have sucessfully copied full Linux installations more times I can count with the fingers in my both hands, including dev, pipe, FIFO and sparse files from one partition/disk to another by using a command incantation such as:
```

rsync -aSHW --inplace /mnt/original/linux/install/. /mnt/target/partition/.

```
Of course, you should never try to copy the partition you are presently running into another, that's a recipe for disaster. If you don't have a second linux installation in a third partition on disk you can boot from a live CD and do it as outlined above. Notice that each and every flag given to rsync is **necessary**, as are the dots at the end of the paths.
 
Don't forget that you need to install your boot loader pointing to the new partition in order to boot from it.

---

### Post by cafevincent on 2005-11-14
> Don't forget that you need to install your boot loader pointing to the new partition in order to boot from it.

Thanks for the help. Is this something I can do from GParted or...?

---

### Post by GTvulse on 2005-11-14
[QUOTE=cafevincent]Thanks for the help. Is this something I can do from GParted or...?[/QUOTE]
No GParted at all. This is really a delicate operation even if dead simple and I need to know the layout of your disks and where is GRUB installed presently (in the MBR or a partition superblock).

---

### Post by cafevincent on 2005-11-14
[QUOTE=dradul]No GParted at all. This is really a delicate operation even if dead simple and I need to know the layout of your disks and where is GRUB installed presently (in the MBR or a partition superblock).[/QUOTE]

Whoa, I'm an absolute beginner so I have absolutely no idea how to get you that information.

---

### Post by cafevincent on 2005-11-18
[QUOTE=dradul]No GParted at all. This is really a delicate operation even if dead simple and I need to know the layout of your disks and where is GRUB installed presently (in the MBR or a partition superblock).[/QUOTE]

I hope fdisk -l helps in knowing the layout, here it is:

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30023   241159716   83  Linux
/dev/hdb2           30024       30401     3036285    5  Extended
/dev/hdb5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4500    36146218+  83  Linux

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4500    36146218+   7  HPFS/NTFS

```

If you need any other info please tell me what command to use to get it printed. The plan is to copy /dev/hdb1 (without my personal files) to /dev/sda1 or to use RAID for /dev/sda1 & /dev/sdb1 (if possible) and install there.

---

