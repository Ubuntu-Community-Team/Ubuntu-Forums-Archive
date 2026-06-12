---
title: "Uninstalling ubuntu"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by obscured47 on 2007-06-13
Hi,

I've got ubuntu installed and realised I have to install stupid windoz too so I'm going for a dual boot on one hard disk. I've read that I have to uninstall ubuntu, then install windows and then ubuntu again. How do I do that without messing up with my boot system etc?

Cheers

---

### Post by Outrunner on 2007-06-13
Simply install Windows over Ubuntu and make sure to leave space for your next Ubuntu installation. Then install Ubuntu normally.

---

### Post by obscured47 on 2007-06-13
i thought there were some tricks there :P
thanks!

---

### Post by luca.mina on 2007-06-13
Hi,

download Gparted Live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) or maybe you can make a grub floppy disk ([http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html))

1.Boot your pc from Gparted LiveCD

2. with gparted make a new NTFS partition on the first hard disk (maybe you have to resize the partition containing ubuntu). remember the number of ubuntu's partition (eg hda1) and windows partition (eg hda2)

3. Then boot with Windows Cd and install it on your new partition

4. Now you have lost Grub from mbr, don't worry. boot from Super Grub Disk and choose to fix boot  of linux (Grub)

if Super Grub Disk fail (I never try this cd) boot from grub floppy disk and then give:

root (hd0,0)     were hd0,0 is ubuntu's partition if you have in hda1, and it means the first hard disk and the first partition. e.g. hd0,1 will be the second partition if you have ubuntu in hda2

setup (hd0)

and then reboot.
now boot from your ubuntu  (if not use live cd like knoppix) and change /boot/grub/menu.lst  (in ubuntu: sudo gedit /boot/grub/menu.lst) and at the end add:

title Windows
hide (hd0,0)
unhide (hd0,1)
rootnoverify (hd0,1)
chainloader +1
makeactive

!! please check you partition number !!!
with this you hide ubuntu's partion hd0,0 (hda1) and unhide windows partition hd0,1 (hda2), then it boot windows [rootnoverify (hd0,1)]

I hope this work.

PS: sorry for my bad english

---

### Post by Roger Gundberg on 2007-06-13
Perhaps you may consider Virtual Box or Virtual Machine. Both fine products.

---

### Post by obscured47 on 2007-06-13
thanks guys!
specially luca.mina :)
gonna try it when have time

---

