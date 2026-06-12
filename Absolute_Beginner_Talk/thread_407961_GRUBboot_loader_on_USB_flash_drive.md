---
title: "GRUB/boot loader on USB flash drive?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by hodgeMN on 2007-04-12
New to Ubuntu but have installed linux in the past.  My question in this:  When I had linux installed before, I intalled the linux boot loader on a diskette and simply booted from the diskette (a drive) when I wanted to run linux.  This way, my MBR was not affected.  I currently have a Dell inspiron 9400 and would like to do a similar set up with a flash drive if possible.  Has anyone done this?

---

### Post by mac.ryan on 2007-04-13
I believe the right procedure would be to install ubuntu from the alternate CD (the standard CD installs grubs stage 1 on MBR of your first HD), then - provided that the alternate CD won't offer you this chance already - you might use [super grub disk]("http://supergrub.forjamari.linex.org/") to install grub on a removable media.

---

### Post by justleen on 2007-04-13
you might wanna have a look at this guide by A.I.
[http://doc.gwos.org/index.php/Edgy_USB_Install](http://doc.gwos.org/index.php/Edgy_USB_Install)

---

