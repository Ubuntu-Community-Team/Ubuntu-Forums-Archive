---
title: "hda1 on Xubuntu / which file system?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by GabrielWolff on 2007-04-23
Hey.

I had my xubuntu crashing, and now I'm trying to mount my hda1 with a live CD.
When trying to mount, it gives me following error:
```
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/hda1 a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
What is the filesystem or how do I find that out?

G

---

### Post by taurus on 2007-04-23
```
sudo fdisk -l
```

---

### Post by GabrielWolff on 2007-04-23
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4864    39070048+   5  Extended
/dev/hda5   *           1          31      248944+  83  Linux
/dev/hda6              32        4864    38821041   8e  Linux LVM
ubuntu@ubuntu:~$ 
```

So waitasec. Is hda1 the right partition to mount if I want to access my Desktop (for example)?
And what do I type in? Obviously not
```
ubuntu@ubuntu:~$ sudo mount -t Extended /dev/hda1 a
```
G

---

### Post by taurus on 2007-04-23
Your /dev/hda1 is an extended partition.  You can't mount an extended partition.  Perhaps you want to mount /dev/hda5 which is an ext3 filesystem, not vfat.

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda5 /mnt/ubuntu
ls -la /mnt/ubuntu
```

---

### Post by GabrielWolff on 2007-04-23
OK, here we go.
I had a look at gparted, and gparted isn-t able to determine the filesystem of hda6 (which is the one I want to actually mount.
It says; File system: Unknown

What now?

---

