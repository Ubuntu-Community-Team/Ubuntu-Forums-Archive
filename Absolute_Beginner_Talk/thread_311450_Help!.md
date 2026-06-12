---
title: "Help!"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by danielmat18 on 2006-12-02
Can I mount my hard drive from a live OS disc version? 
Big D

---

### Post by tocleora on 2006-12-02
You *should* be able to.  Go to System > Administration > Disks and try it there.

---

### Post by danielmat18 on 2006-12-02
> **tocleora said:**
> You *should* be able to.  Go to System > Administration > Disks and try it there.

Yeah, not seeing it? What should I do now?

---

### Post by mmmichael on 2006-12-02
open a terminal (Applications>Accessories>Terminal) and enter
```
sudo mkdir /mnt/hda1
```
```
sudo mount -t ext3 /dev/hda1 /mnt/hda1
```

Then click on Places>Computer, double click Filesystem, then double click mnt, then hda1. Assuming that you are using an Ubuntu live cd and you are trying to access an ext3 filesystem on partition hda1, this should display its contents.

---

### Post by aysiu on 2006-12-02
Let's take it one step at a time.

Can you post the output of this terminal command? ```
sudo fdisk -l
```

---

### Post by danielmat18 on 2006-12-02
> **aysiu said:**
> Let's take it one step at a time.

Can you post the output of this terminal command? ```
sudo fdisk -l
```

Will this Work
> [INDENT]Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

[/INDENT]

---

### Post by aysiu on 2006-12-03
Make sure you're pasting in the command: ```
sudo fdisk -l
``` That last one is a hyphen and a lowercase *L*, not a capital *i* or the number one.

---

### Post by danielmat18 on 2006-12-04
> **aysiu said:**
> Make sure you're pasting in the command: ```
sudo fdisk -l
``` That last one is a hyphen and a lowercase *L*, not a capital *i* or the number one.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996    b  W95 FAT32
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

This will work right?

---

### Post by aysiu on 2006-12-04
You have a swap partition and a FAT32 partition? Where's Ubuntu installed to? Or maybe it isn't yet?

Well, to mount the FAT32 partition, paste these commands in the terminal: ```
sudo mkdir /media/recovery
sudo mount -t vfat /dev/hda1 /media/recovery -o iocharset=utf8,umask=0222
```

---

