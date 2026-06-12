---
title: "Sometimes Ubuntu won't start for me.."
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Oklin on 2006-12-29
It is weird, i have installed Ubuntu and it is working.. but 1 out of 5 times it won't enter Ubuntu it stops at the loading page.. this is what comes:

```
Loading essential drivers...        ok
Mounting root filesystem...
Waiting for root file system...
```

and then it stops for a while, after a few min. a black page comes with this:
```

Booting 'Ubuntus karnel 2.6.15-27-3861
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
karnel /boot/vmlinuz-2.6.15-27-386 root= /der/hda1 ro quiet slash
[Linuz-bz Image, setup = 0x1c00, size 0x157860]
initrd /boot/initrd.img-2.6.15-27-386
[Linux-initrd @ 0,1f979000, 0x676353 bytes]
Save default
boot
uncompressing Linux... ok, booting the karnel.

ALERT! /der/hda1 does not exist. Droppng to a shell!
BusyBox v1.01 (debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built'in commands
/bin/sh: can't access ttx;job control turned off
#
```

I'm very new to Linux so i dont' know what the problem is, since it works sometimes and other times this error comes..

---

### Post by Sef on 2006-12-29
> ALERT! /der/hda1 does not exist. Droppng to a shell!

That line is not correct.  It should read /dev/hda1, not /der/hda1.   Not sure why it does that or what to do about it though.   Use google or ask.com to find out more.

---

### Post by raul_ on 2006-12-29
Just change the line in /boot/grub/menu.lst  (when it doesn't start) and then run update-grub

---

### Post by Oklin on 2006-12-29
> **Sef said:**
> That line is not correct.  It should read /dev/hda1, not /der/hda1.   Not sure why it does that or what to do about it though.   Use google or ask.com to find out more.

my bad it IS "/dev/hda1"

> **raul_ said:**
> Just change the line in /boot/grub/menu.lst  (when it doesn't start) and then run update-grub

you wan't me to write "/boot/grub/menu.lst" when i get the error?.. I tried that but nothing happends.. I'm new to Linux so please explain what exactly i need to do..

---

### Post by raul_ on 2006-12-29
I thought that the line was wrong :P [http://www.ubuntuforums.org/showthread.php?t=197956]("http://www.ubuntuforums.org/showthread.php?t=197956")

---

