---
title: "Grub is blind as a bat (error 15: file not found)"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by anandus on 2007-09-22
Ok, I've got this strange problem.

When booting GRUB can't find a file. I've walked through menu.lst, devices.map, 'fdisk -l', etc.etc.
And it should work.

Ubuntu is installed on the first SATA-disk (hd2 in devices.map), first partition (so hd(2,0)), and it's correct everywhere. The initrdblahbla and the vmlinuzblahblah are in the right place and the names correspond with the names in menu.lst

So what did I miss?

Thanks a bunch!

Addendum:
device.map:
```
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda
(hd3)	/dev/sdb
```

Last bit of menu.lst:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ade49d91-9a52-498f-923d-9a03f17c5397 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ade49d91-9a52-498f-923d-9a03f17c5397 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
```

ls /boot/ (on sda):
```
abi-2.6.20-15-generic         initrd.img-2.6.20-15-generic.bak
config-2.6.20-15-generic      memtest86+.bin
grub                          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic  vmlinuz-2.6.20-15-generic
```

ls /boot/grub/ (on sda):
```
default        fat_stage1_5       menu.lst           stage1
device.map     installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5
```

sudo fdisk -l:
```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30401   244196001   83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  83  Linux

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
```

so what did I (or actually GRUB :p ) miss?

---

### Post by Malta paul on 2007-09-22
Hi, you could try changing 'root to 0,2'
Hope this works:wink:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by anandus on 2007-09-22
> **Malta paul said:**
> Hi, you could try changing 'root to 0,2'
Hope this works:wink:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)You mean in grub?
eg.: grub> root (hd0,2) ?
(it replies, ofcourse, 'no such partition')

Or do you mean something else?

---

### Post by skymera on 2007-09-22
it should work
HD 1 partition 3 (hd0,2)

---

### Post by anandus on 2007-09-22
> **skymera said:**
> it should work
HD 1 partition 3 (hd0,2)It gives the 'no such partition' :(

But do you imply that you can just add partitions on different hard disks as being partitions on the first hard disk? :)

An odd thing I just noticed, by the way, is I manually tried to boot from the different hard disks (F8 at POST on my motherboard gives me the choice what disk to boot), And to my surprise hdc1 booted with grub! (gave same error 15, though, which is logical as there's only music on the disk).

How did (another?) grub end up there and why does it boot, even without the 'boot'-flag?

---

