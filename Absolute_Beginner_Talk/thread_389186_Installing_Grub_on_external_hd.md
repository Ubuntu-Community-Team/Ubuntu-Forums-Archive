---
title: "Installing Grub on external hd"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ubuntukid on 2007-03-20
I've been trying to install ubuntu to an external hard drive but the installer always fails when it's time to install grub. Before the installation starts I change the GRUB install path from hd0 (because I want to leave the windows mbr untouched) and typed in sd0. This failed, so I tried sda, but that also failed. My external hard drive connects via usb and gets the name sda. What device name to I give grub to have it install onto the external hd?

---

### Post by benerivo on 2007-03-20
Try changing the BIOS to boot from the usb drive and physically unplug the internal drive from the motherboard. Then Ubuntu should have no option but to install GRUB to the external drive, and it might work...

The problem may be related to the Ubuntu installer not recognising the usb drive.

---

### Post by confused57 on 2007-03-20
> **ubuntukid said:**
> I've been trying to install ubuntu to an external hard drive but the installer always fails when it's time to install grub. Before the installation starts I change the GRUB install path from hd0 (because I want to leave the windows mbr untouched) and typed in sd0. This failed, so I tried sda, but that also failed. My external hard drive connects via usb and gets the name sda. What device name to I give grub to have it install onto the external hd?

/dev/sda should install grub to your external drive mbr...or you could use the live cd to install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

When you boot first to your external drive, you may have to edit the root partition in grub:
highlight your Ubuntu entry in the grub menu at startup, press "e" to edit, then change root from (hd1,x) to (hd0,x), then press "b" to boot...in other words, booting first to your external drive will cause grub to recognize it as hd0.  This change is only temporary, if it works, you can make it permanent in your /boot/grub/menu.lst.

---

