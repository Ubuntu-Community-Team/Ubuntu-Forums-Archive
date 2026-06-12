---
title: "Installing Xubuntu with older BIOS"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-12-15
I'm trying to help a friend resurrect an old laptop with Xubuntu.  I need to use the alternate CD because of memory issues but my big problem is that the antiquated BIOS wont allow to boot from the CD.  It only allows HD->FD booting.

The laptop is running Windows 98 right now but the HD is so small, I want to avoid installing with Wubi.  I would rather do a clean install.

Any suggestions?

---

### Post by Beaucephus on 2007-12-15
If the LT has a floppy drive you can create a boot floppy.  That is the old school way.

---

### Post by logos34 on 2007-12-15
Try Smart Boot Manager

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by djen9999 on 2007-12-15
No, I should have mentioned that there is no FD.  There's a port for an external but nothing internal.

---

### Post by logos34 on 2007-12-15
> **djen9999 said:**
> No, I should have mentioned that there is no FD.  There's a port for an external but nothing internal.

How big is hard disk? And how much free space?

---

### Post by djen9999 on 2007-12-15
The HD has 2 GB.  Most of it is taken up with old files that can be deleted.  Right now there's less than 700 MB left on the drive.

---

### Post by logos34 on 2007-12-15
I was going to suggest a installation from hard drive (from windows), but with that tiny thing, forget it.  You've got no wiggle room
> 
"[To install Xubuntu, you need 1.5 GB of free space on your hard disk.]("http://www.xubuntu.org/get")"

Either find a way to hook up a floppy drive (usb floppy won't work because you probably can't boot from usb), or get a bigger hard disk.

ADD: the only other way is to tak the HDD out and connect it to another pc.  Install xubuntu on the entire drive, wiping win98.  Then put it back in the old lappy and pray that fixing the graphics driver is all that will be needed to get it to run properly (i.e. sudo dpkg-reconfigure xserver-xorg).

---

### Post by djen9999 on 2007-12-15
Yep, that looks like my only option.  This was just a project we were working on to see what could be done.  The LT was given to him by one of his clients so there's no investment lost.

Thanks all.

---

### Post by gn2 on 2007-12-15
Try Zenwalk, I did this: [http://support.zenwalk.org/index.php?topic=12923.0](http://support.zenwalk.org/index.php?topic=12923.0)

---

