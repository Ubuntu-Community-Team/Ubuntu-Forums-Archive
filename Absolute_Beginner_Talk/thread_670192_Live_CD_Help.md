---
title: "Live CD Help"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by rmanor on 2008-01-17
Hi,

I've download Mono Live CD which uses Ubuntu, and I'm have some questions.

How do I access my hard drive? 
I have WindowsXp on that computer, so the filesystem is NTFS.
When I try to access the mounted drive, I get a permission denied error.

Also, is there any way to access a usb drive ?

thanks.

---

### Post by jken146 on 2008-01-17
The command ```
sudo fdisk -l
``` shows hour hard drives and their partitions.

To mount a partition use the mount command.  For example, to mount an ext3 partition sda2 onto the folder /mnt, you would type ```
sudo mount -t ext3 /dev/sda2 /mnt
```

Most USB devices (mass storage ones) will automount when you plug them in.  An icon will appear on the desktop.

You can check which devices are mounted by typing ```
mount
```

---

