---
title: "GRUB Error 11 Unrecognized device"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by imuro on 2007-06-29
I follow the guide ([http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)) to install ubuntu feisty fawn on a raid 0 system. The first time I installed the boot freezes. After reading the comments in the guide i add in the line "/sbin/udevsettle --timeout 10" to _the end of_ the file /usr/share/initramfs-tools/scripts/init-premount/udev. 


This time the boot just went to a straight error 11 and didnt go further but vista boots fine. 
my menu.lst look something like this:


# Sun Jan 28 06:28:23 EST 2007
default 0
timeout 8
title Ubuntu Linux
root (hd0,4)
kernel /vmlinuz root=/dev/mapper/isw_dgcbheejgc_Volume07 ro dodmraid
initrd /initrd.img
title Windows
rootnoverify (hd0,0)
chainloader +1


Does this have something to do with dmraid? Any help appreciated!!

Thanks in advance,
Chris

---

### Post by alienexplorers on 2007-06-30
Your menulist should look something like this:
> title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

