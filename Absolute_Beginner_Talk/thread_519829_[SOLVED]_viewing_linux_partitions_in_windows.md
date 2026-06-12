---
title: "[SOLVED] viewing linux partitions in windows"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by johnnybgood115 on 2007-08-07
All, 

I am using a Lenovo T43 with two hard drives.  One is my original NTFS running windows and the other is a FAT32 running Ubuntu 7.  

I have already configured my Linux to view the NTFS drive and have it read/write.  I am hoping there is a way to view the FAT32 file system in Windows. 

I basically want to be able to trade files between both operate systems regardless of which OS i'm using.  In windows, the drive does not even come up in My Computer. 

Thanks in advance.

---

### Post by trak87 on 2007-08-07
Fat32 is a Microsoft file format. You probably meant your second drive has Linux on an ext3 file system.

This will show all the detected drives:

```
sudo fdisk -l
```

What does yours show?

---

### Post by Inxsible on 2007-08-07
trak is right. You probably meant EXT3.

well you need to install [Fs-Driver]("http://fs-driver.org/") in Windows partition to be able to access the EXT3 drives.

---

### Post by johnnybgood115 on 2007-08-07
This is the output for     fdisk -l


```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7086    53570128+   7  HPFS/NTFS
/dev/sda2            7087        7751     5027400   12  Compaq diagnostics

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6992    56163208+  83  Linux
/dev/sdb2            6993        7296     2441880    5  Extended
/dev/sdb5            6993        7296     2441848+  82  Linux swap / Solaris

```

---

### Post by Skrypt on 2007-08-07
> **Inxsible said:**
> trak is right. You probably meant EXT3.

well you need to install [Fs-Driver]("http://fs-driver.org/") in Windows partition to be able to access the EXT3 drives.

What he said. You'll have to assign a drive letter but it's really simple and straight forward and works like a charm.

If you've not found something your windows partition, use ntfs-3g.

---

### Post by johnnybgood115 on 2007-08-07
thanks,
worked great!!

---

### Post by Inxsible on 2007-08-07
> **johnnybgood115 said:**
> thanks,
worked great!!

Cool, make sure you mark your thread as solved for someone else :)

---

