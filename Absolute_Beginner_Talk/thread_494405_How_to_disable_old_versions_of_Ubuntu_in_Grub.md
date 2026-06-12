---
title: "How to disable old versions of Ubuntu in Grub?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by krazedj on 2007-07-06
I am of course a N00b to linux and Ubuntu. I just got Ubuntu installed, dual booting between Vista and Ubuntu. UBuntu ran through some updates and now there is an older version still listed in the grub menu. I would like for the menu to only say Ubuntu 7.04 and Windows Vista.
Everything else can be hidden. How do I do this?

---

### Post by inuyokai on 2007-07-06
This post might help you - [http://ubuntuforums.org/showthread.php?t=494371](http://ubuntuforums.org/showthread.php?t=494371).

I think its something to do with editing the boot/grub/menu.list file though.

---

### Post by krazedj on 2007-07-06
OK, I get how to enable my Vista as the default OS (I already had that configured). I still need to know how to hide an OS in Grub. There must be a disable command in grub or something.

---

### Post by dpar on 2007-07-06
Comment out the entries that you don't want to see with a '#'

---

### Post by macogw on 2007-07-07
If you have a ton of old ones, you can uninstall the really old kernels, and they'll automatically disappear from GRUB.  Keep one old one around though as a backup in case something breaks.

---

### Post by fumduck on 2007-07-07
sudo gedit /boot/grub/menu.lst   (copy and paste into terminal..... applications button --> accessories--> terminal)  enter password  and hit  enter

Gets  you the   menu list.. at the bottom of that you get the boot loader selection like so  (mine)

## ## End Default Options ##

t
title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP/ Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title linux
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda3  acpi=on resume=/dev/sdb3 splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title linux-nonfb
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda3  acpi=on resume=/dev/sdb3
initrd (hd0,2)/boot/initrd.img

title failsafe
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda3  failsafe acpi=on resume=/dev/sdb3
initrd (hd0,2)/boot/initrd.img

 edit the ubuntu you don'y want.. save..  Oh yeah and make sure to make a backup ...just in case..Its in the order of the boot screen.. so should be fairly easy to figure out which one you don't want..

Hope that helps..

---

