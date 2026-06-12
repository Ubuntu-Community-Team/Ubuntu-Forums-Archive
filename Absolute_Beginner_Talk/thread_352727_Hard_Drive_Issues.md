---
title: "Hard Drive Issues"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Baphijmm on 2007-02-03
I am not entirely new to Ubuntu; I've been using it for almost a year now.  However, I am fairly new to 6.10; the last udgrade I had on here was the one before Dapper, I honestly can't remember its name.

Anyway, in this previous release, there had been an option in System->Administration called "Disks" with which I could re-mount my second hard drive with no problem.  I cannot find this option any more.  I had remounted the drive several weeks ago, but have since restarted my computer and forgotten how I did it.  This is where I need help.

The drive has only one partition, /hdb1.

> ~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         392     3148708+   7  HPFS/NTFS
/dev/hda2             393        1608     9767520   83  Linux
/dev/hda3            1609        4865    26161852+   5  Extended
/dev/hda5            1609        1705      779121   82  Linux swap / Solaris
/dev/hda6            1706        4865    25382668+   b  W95 FAT32

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux

As I said, I had no problems with this before, but am completely lost now.  Any help would be greatly appreciated.

---

### Post by taurus on 2007-02-03
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it and create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Baphijmm on 2007-02-03
Thank you very much!  That appears to have fixed it.

---

