---
title: "Mounting an NTFS harddrive."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Brewbart on 2007-03-10
I am trying to mount my windows partition which is an NTFS.  I use cmd: sudo fdisk -l and get:
Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14569   117025461   83  Linux
/dev/hdb2           14570       14946     3028252+   5  Extended
/dev/hdb5           14570       14946     3028221   82  Linux swap / Solaris

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10011    80413326    7  HPFS/NTFS

Where do i go from here to mount the drive?  This is my first time attempting to do this on this install of linux.  Thanks a lot

---

### Post by taurus on 2007-03-10
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

