---
title: "Boot Windows from second SATA Drive"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2007-05-02
Hi. I have two SATA drives on my desktop. 1st one is 250GB Ubuntu Drive, 2nd is a 60 GB Windows XP drive. I can not get grub to load up Windows XP. 
maybe this will help


> red@red-desktop:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29379   235986786   83  Linux
/dev/sda2           29380       30515     9124920    5  Extended
/dev/sda5           29380       30515     9124888+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056    7  HPFS/NTFS
red@red-desktop:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
red@red-desktop:~$ 


> red@red-desktop:~$ sudo gedit /boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=faf56b73-2d00-4b57-87b6-0475eff6abef ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=faf56b73-2d00-4b57-87b6-0475eff6abef ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

Maybe this helps, I just want to know what I have to enter into my  /boot/grub/menu.lst to get xp to load

---

### Post by etherior on 2007-05-02
I think you should put this in your /boot/grub/menu.lst:


title Windows( or wherever you want)
rootnoverify (hd1,0)
chainloader +1

if after this you receive an error like this:
root (hd1,0)
Filesystem type unknown, partition type 0x7
chainloader +1

or similar,
try to change your /boot/grub/menu.lst with:
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

Also remember that windows needs a partition with the bootable flag.

---

### Post by mahiyar on 2007-05-02
I used this entry to boot my non first windows disk. I have one sata (Ubuntu feisty) + ide (Windows + Ubuntu edgy). I boot from sata.
 

[SIZE=2]title Windows XP[/SIZE]
[SIZE=2]root (hd1,0)[/SIZE]
[SIZE=2]savedefault[/SIZE]
[SIZE=2]makeactive[/SIZE]
[SIZE=2]map (hd0) (hd1)[/SIZE]
[SIZE=2]map (hd1) (hd0)[/SIZE]
[SIZE=2]chainloader +1[/SIZE]
 
If you are using edgy I guess its ok but in feisty there seems to be some changes in grub's menu.lst. A good site to learn about grub is here => [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by neufelry on 2007-05-02
> **mahiyar said:**
> 

[SIZE=2]title Windows XP[/SIZE]
[SIZE=2]root (hd1,0)[/SIZE]
[SIZE=2]savedefault[/SIZE]
[SIZE=2]makeactive[/SIZE]
[SIZE=2]map (hd0) (hd1)[/SIZE]
[SIZE=2]map (hd1) (hd0)[/SIZE]
[SIZE=2]chainloader +1[/SIZE]


My situation is also dual boot, two sata drives, xp on the second. I use fiesty and I found the rootnoverify method does not work while this one does.

---

### Post by redDEADresolve on 2007-05-02
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


worked perfectly thanks

---

