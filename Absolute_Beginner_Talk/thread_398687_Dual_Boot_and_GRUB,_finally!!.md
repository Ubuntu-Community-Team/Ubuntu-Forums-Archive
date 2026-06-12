---
title: "Dual Boot and GRUB, finally!!"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Jim D v2.0 on 2007-04-01
This post is for anyone that has the same configuration as me and is having problems with GRUB. It took me a fair amount of experimentation and trial and error to finally get it right. This works for me and I hope this helps someone else.

My configuration:
Primary IDE Master : 40 GB with Win2K, ntfs
Primary IDE Slave : 150 GB, ext3
Secondary IDE Master : 40 GB, Ubuntu 6.10, ext3
Secondary IDE Slave : CD-ROM

BIOS has the first boot drive as Secondary IDE Master.

What follows is the contents of menu.lst (most of the comments removed for posting purposes)

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Windows 2000
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

here is the contents of fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=926d61dd-6d63-4b1d-b80f-c8280c8b1814 /               ext3    defaults,erro$
# /dev/hdc5
UUID=43315ab0-f2eb-45c1-ba01-c6c624de2e36 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5       /media/drive0   ext3    defaults        0       2
/dev/hdb6       /media/drive1   ext3    defaults        0       2
/dev/hda1       /media/win2k    ntfs    nls=utf8,fmask=0333,dmask=0222  0      $
/dev/hdb5       /home           ext3    nodev,nosuid    0       2

---

### Post by diepruis on 2007-04-01
Congrats. Had fun? ;)

---

### Post by Jim D v2.0 on 2007-04-01
It was interesting and occasionally frustrating. But, a good learning experience.

---

