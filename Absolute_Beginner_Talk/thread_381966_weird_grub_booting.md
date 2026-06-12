---
title: "weird grub booting"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Russellvg on 2007-03-11
my computer has windows xp and xubuntu linux on it, it also has xubuntu linux on a 2 gig usb flash disk. When i start my system with the usb flash disk in grub starts and i choose linux on my my usb flash disk it says error 17: cannot mount partition. but when i start my system with an xubuntu live cd in, let it boot the cd, and choose boot from first hard disk, it starts grub. I choose to boot from the usb flash drive and it works.  why do i need to boot from the xubuntu cd to boot into my usb flash drive??

---

### Post by dstew on 2007-03-11
My guess is that your root assignment to grub in your /boot/grub/menu.lst file is accurate only when you boot from the hard disk.

Is your flash drive bootable? Is it listed before your hard disk in the BIOS boot order? If you have two linux systems on your computer, which it sounds like you do, is the Ubuntu linux entry in your menu.lst files the same on both, or different?

---

