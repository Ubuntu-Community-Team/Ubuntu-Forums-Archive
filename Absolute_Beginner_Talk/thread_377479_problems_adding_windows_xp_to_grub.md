---
title: "problems adding windows xp to grub"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Xetroc on 2007-03-06
Hello,

I'm having some trouble getting windows xp added to grup, hope you can help. When i select windows xp from the grub menu, i get the following error; "Error 21: Selected disk does not exist"

```
-----@---:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       10199    81923436   83  Linux
/dev/hda2           10200       10329     1044225   82  Linux swap / Solaris
/dev/hda3   *       10330       12160    14707507+   7  HPFS/NTFS
```

```
-----@---:~$ sudo gedit /boot/grub/menu.lst
```

```
title		Alternative OS
root		(hd3,0)
makeactive
chainloader	+1
```

---

### Post by buuntuu! on 2007-03-06
The grub entry should be hd(0,3) if i am not mistaken...
did you install xp AFTERWARDS or why is it listed as hda3?

---

### Post by ikey on 2007-03-06
For grub, hda is hd0, the number after that is the partition but it is zero-based.
In short you should have (hd0,2) to select hda3 as disk to boot from.

---

### Post by Xetroc on 2007-03-06
Yes installed windows xp after ubuntu.

It's (hd0,0) according to this link, and the example from menu.lst

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu")

```
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
```

---

### Post by proalan on 2007-03-06
try this

title		windows xp
root		(hd0,3)
makeactive
chainloader	+1

---

### Post by Xetroc on 2007-03-06
> **ikey said:**
> For grub, hda is hd0, the number after that is the partition but it is zero-based.
In short you should have (hd0,2) to select hda3 as disk to boot from.

Oh thanks, I will try that now.

---

### Post by proalan on 2007-03-06
oops

> root (hd0,3)

should be

root (hd0,2)

---

### Post by buuntuu! on 2007-03-06
> **ikey said:**
> For grub, hda is hd0, the number after that is the partition but it is zero-based.
In short you should have (hd0,2) to select hda3 as disk to boot from.

ikey is right, my fault! hd0,2 it is!

i thought installing window$ afterwards would kill a linux partition!
how did you do it??

---

### Post by Xetroc on 2007-03-06
> **ikey said:**
> For grub, hda is hd0, the number after that is the partition but it is zero-based.
In short you should have (hd0,2) to select hda3 as disk to boot from.

Worked great. Thanks.

---

### Post by Xetroc on 2007-03-06
> **buuntuu! said:**
> ikey is right, my fault! hd0,2 it is!

i thought installing window$ afterwards would kill a linux partition!
how did you do it??

When you install linux, have some spare hdd space for a windows partition.


Getting grup up and running again after windows install:
1) Install windows
2) Boot linux from live cd
3) sudo fdisk -l
4) sudo mount /dev/hda[x] /mnt  ...... (hda[x] is your linux partition, you can see it by doing pt.3)
5) sudo group-install --root-directory=/mtn /dev/hda

---

### Post by proalan on 2007-03-06
This is a handy automated boot manager recovery disk for the lazy ones like me

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html]("http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html")

---

