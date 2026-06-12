---
title: "Files and Directories"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by LAF4U on 2007-04-17
Hi,

I'm in UBUNTU right now. And I'm wondering how to see all the files and directories on my LOCAL HARD drive. I'm running UBUNTU on my USB key.

I'm doing Places> Computer... But I don't see my Hard Drive in there.

Please Help!

:(

---

### Post by taurus on 2007-04-17
You need to mount it before you can view it.  What's the output of this command from a terminal and which partition you want to mount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by LAF4U on 2007-04-17
> **taurus said:**
> You need to mount it before you can view it.  What's the output of this command from a terminal and which partition you want to mount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Here you go:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 1463 MB, 1463648256 bytes
255 heads, 63 sectors/track, 177 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          92      738958+   6  FAT16
/dev/sdb2              93         177      682762+  83  Linux


Thanks.

---

### Post by taurus on 2007-04-17
From a terminal, type

```
sudo mkdir /media/sda1 /media/sdb1
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by LAF4U on 2007-04-17
> **taurus said:**
> From a terminal, type

```
sudo mkdir /media/sda1 /media/sdb1
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
df -h
```

Thanks...

Will I have to do this everytime I log into UBUNTU???

And...

How can I see my HARD DRIVE now, from Places> Computer>

:confused:

---

### Post by taurus on 2007-04-17
You can edit /etc/fstab

[code[gksudo gedit /etc/fstab[/code]
and add these two lines to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
```
Then, they will be mount automatically each time you boot Ubuntu.

There should be two icons on your desktop, one for /dev/sda1 and the other for /dev/sdb1.

---

