---
title: "Vista / Ebuntu Edgy Dual Boot"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by WicKeDcHilD on 2007-04-10
Ok starters i am new to ubuntu been using it for less then a week and love. I came from Windows and can say i want to stay with edgy but here is where my problem starts. Some programs i am still to stuck on to leave windows all together so today i did a dual boot from scratch, installing vista first and then edgy using this guide to help me.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Everything went smoothly and i got edgy loaded... Now i cant access my frickin windows partition, edgy works nice but when i try to log into windows it reboots when it should be loading the windows boot screen ( does that over and over till i force edgy  to load )...

here is my sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13878   111472640    7  HPFS/NTFS
/dev/sda2           13879       24133    82373287+  83  Linux
/dev/sda3           24134       24321     1510110    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris

and here is my sudo gedit /boot/grub/menu.lst

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

title		Windows Vista
root            (hd0,0)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

# title		Other operating systems:
# root

I seen somewhere else on the forums that if i set my windows to what it is below it might work but when i did all it did was hang instead of reboot or loading ( so i changed it back )...

title		Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader	+1

Someone help me please Lol

---

### Post by WicKeDcHilD on 2007-04-10
bumpity bump

---

### Post by grkravi on 2007-04-10
Do you have a Dell laptop ? 
My entry in menu.lst is :

title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Though it says XP, its actually Vista's boot loader, i multi boot my laptop with XP, Edgy and Vista. Try specifying (hd0,1).

---

### Post by Austin_KW on 2007-04-11
Did you resize the vista partition to install ubuntu if so look at this thread  [http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122) about running ntfsfix

---

