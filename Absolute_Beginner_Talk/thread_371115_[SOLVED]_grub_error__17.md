---
title: "[SOLVED] grub error  17"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-02-26
hello all

you have all helped me fix a grub error before maybe u can help againn


ubuntu has been working fine untill i used gparted. i used gparted and made the ubuntu partion smaller

it worked fine because i then logged back in to ubuntu.

i turned off the computer and this moring i booted it up into ubuntu and i got 

"Grub loading please wait...
Grub Error 17"

PLEASE HELP!!

---

### Post by mikewhatever on 2007-02-26
Is the Ubuntu partition primary or logical? Have you created another partition in the freed space?

---

### Post by confused57 on 2007-02-26
> **gameman12 said:**
> hello all

you have all helped me fix a grub error before maybe u can help againn


ubuntu has been working fine untill i used gparted. i used gparted and made the ubuntu partion smaller

it worked fine because i then logged back in to ubuntu.

i turned off the computer and this moring i booted it up into ubuntu and i got 

"Grub loading please wait...
Grub Error 17"

PLEASE HELP!!
Hello  gameman12,
You might want to boot up the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

This will show your new partition table on your Ubuntu drive...also, gparted would show your partitions.

---

### Post by drs305 on 2007-02-26
I am new to Linux and when I was attempting to set up a dual boot system I found a resource called Super Grub. It helped me create a disk that helped me analyze boot problems, including partition errors. The address for the current version is: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by gameman12 on 2007-02-26
confused is helping me again with the same error,

i'm embarased......

here's the output

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           6       48163+  de  Dell Utility
/dev/hdc2   *           7        9336    74943225    7  HPFS/NTFS
/dev/hdc3            9337        9729     3156772+  db  CP/M / CTOS / ...

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15803   126937566    7  HPFS/NTFS
/dev/sda2   *       24619       29929    42660607+  83  Linux
/dev/sda3           29930       30401     3791340    5  Extended
/dev/sda5           29930       30401     3791308+  82  Linux swap / Solaris

---

### Post by Patrick K on 2007-02-26
When I resized my partitions, the partition names were changed. Which  caused Grub problems (error 17). Try comparing fstab with menu.lst. Maybe you can see a discrepancy somewhere. GParted might help with this, don't change anything just see what it has named the partitions.

---

### Post by gameman12 on 2007-02-26
i'll try that, what if i find a descrepincy???

---

### Post by Patrick K on 2007-02-26
You'll need to correct menu.lst to reflect the actual configuration of the partitions.

---

### Post by gameman12 on 2007-02-26
i have a really dumb noob question

can u post the commands to view menu.lst and fstab.

i  also forgot the commands to be able to save the changes i made..

sry bout my dumb noob questions

---

### Post by confused57 on 2007-02-26
> **gameman12 said:**
> i have a really dumb noob question

can u post the commands to view menu.lst and fstab.

i  also forgot the commands to be able to save the changes i made..

sry bout my dumb noob questions

You can try editing the grub menu at bootup...highlight your Ubuntu entry, press "e" to edit, then change the line with root to (hd0,1), then press "b" to boot.  You can make the changes permanent in your /boot/grub/menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Hope this helps...looks like you made a new partition at the beginning of the hard drive, which would change the root partition from (hd0,0) to (hd0,1).

This website has a thorough explanation of grub(see the section entitled thusly):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by gameman12 on 2007-02-27
thx confused for helping.

i did that and ubuntu started too boot and i got an error i've never gotten before, i couldn't even boot into recovery mode.

i got an error that looked like this

Busy Box v1.1.3 bulit in shell (ash)
/bin/sh:can't access tty: job control turned off

i bet i did something when i was tinkering......sry


any suggestions?

---

