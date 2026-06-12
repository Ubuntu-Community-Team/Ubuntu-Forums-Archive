---
title: "linux boot"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by winsane on 2007-09-12
Is it possible to boot Ubuntu off of a USB flash drive?  How big would it have to be (I have an 8 GB)...?

---

### Post by Jimmy Carter on 2007-09-12
I tryed the same thing at first, I just got a 500gb drive and I tryed to boot the iso from that, but I wouldnt work. You're best bet is to just burn it to a cd and install from there.

---

### Post by BrendanM on 2007-09-12
If your bios supports booting off a USB drive, it should work, but you'll have to use a custom program to write a bootsector to the USB key in order to make it bootable. In other words, both the BIOS and the USB key have to be set up correctly.

Also, you can't just throw the .iso onto the key. You'll have to extract its contents to the drive.

If you want to install Ubuntu without wasting a CD, and you already have a working OS/internet connection on that computer, you should check out [Wubi]("http://wubi-installer.org/") or [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html")

---

### Post by ravenwere on 2007-09-12
See the following for tutorials:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

