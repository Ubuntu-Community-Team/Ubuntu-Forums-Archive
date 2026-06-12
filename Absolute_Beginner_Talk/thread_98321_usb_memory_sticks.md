---
title: "usb memory sticks"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by M2C on 2005-12-02
Just loaded Ub5.10 - all USB ports are seen in systems manager but can't get to mount the memory stick - which its vendor says supports linux - any suggestions please?
thanks m2c

---

### Post by aysiu on 2005-12-03
Theoretically, when plugged in, a USB memory stick would automount with an icon for it appearing on the desktop.

Something's wrong. Can you plug the USB stick in and copy and paste to this thread the output of the following commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` The terminal is in Application > Accessories > Terminal

---

### Post by M2C on 2005-12-04
[QUOTE=aysiu]Theoretically, when plugged in, a USB memory stick would automount with an icon for it appearing on the desktop.

Something's wrong. Can you plug the USB stick in and copy and paste to this thread the output of the following commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` The terminal is in Application > Accessories > Terminal[/QUOTE]


Thanks will try this - been off line for a few days and will report back
M2C

---

### Post by everklear on 2005-12-05
Not trying to take over the thread, but I'm having a similar problem.  I've determined (using the "fdisk -l" command above, and gparted) that the USB memory stick shows up as /dev/sdd1

It does not automount when I plug it in.

Here is the output from the three commands aysiu mentions - sdd is at the bottom of the fdisk output.  I also have a 160GB USB hard drive attached - it's sdb.

```
fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825        6256    19535040   83  Linux
/dev/hda3            6257       19929   109828372+   7  HPFS/NTFS

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       11502    92389783+   c  W95 FAT32 (LBA)
/dev/hdc2           11503       14946    27663930    f  W95 Ext'd (LBA)
/dev/hdc5           11503       11515      104391   83  Linux
/dev/hdc6           11516       11770     2048256   82  Linux swap / Solaris
/dev/hdc7           11771       14946    25511188+  83  Linux

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19452   156248158+   6  FAT16

Disk /dev/sdd: 262 MB, 262144000 bytes
32 heads, 33 sectors/track, 484 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         485      255984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)


```

```
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              19G   13G  5.2G  71% /
tmpfs                 507M  4.0K  507M   1% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hdc1              89G   72G   17G  82% /mnt/hdc1
/dev/sdb1             149G  7.4G  142G   5% /media/usbdisk

```

```
cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /mnt/hdc1       vfat    nodev,noexec,nosuid,uid=root,gid=root,umask=0000 0 0

```

I am able to manually mount the drive (as root) like so:
```
mount -t vfat /dev/sdd1 /mnt/thumb
```
where I have previously made the mountpoint /mnt/thumb.

Any ideas why this device won't automount?

---

### Post by ssam on 2005-12-05
>    Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         485      255984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)


looks like it could be the problem.

you might want to backup the data and reformat the stick, either in windows or linux (i recomend gparted)

---

