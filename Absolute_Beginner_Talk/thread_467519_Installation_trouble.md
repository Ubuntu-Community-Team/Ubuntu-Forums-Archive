---
title: "Installation trouble"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Bullfrog245 on 2007-06-07
Hi guys,

I am trying to install Ubuntu 7.04 but I am having trouble.  I have an ATI x800 graphics card, so I downloaded the alternate CD as the sticky topic suggested.  When I select text install at the boot menu, the computer loads the kernel, then gives this error:

[     2.493287] usb 1-1: device not accepting address 2, error -71

I have 4 hard drives installed, but I plan on installing on the same hard drive that Windows is on.  I already partitioned it, assigning no file system to the blank half.  I am using an ASUS P5GDC motherboard, and I have a printer, keyboard, and mouse plugged into the USB ports.

Any suggestions?


EDIT: I unplugged the printer, and after the kernel loading screen, the cursor blinked in the upper left corner, and that was it.  The same thing happened when I tried to check the CD contents.  Is the CD or downloaded file bad?

EDIT2: I tried to load windows again so that I could check the downloaded file, but now a screen pops up that says grub> _ and windows doesn't load.  Any suggestions on that too?

---

### Post by confused57 on 2007-06-07
Here's how to restore your Window's IPL to the mbr, so you can boot Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

An excellent guide for downloading & burning an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I'm not sure what's going on...you must have gotten most of the way through the alternate cd install for grub to have been installed on your mbr?

---

### Post by Bullfrog245 on 2007-06-07
I saw no progress bar or anything.  I had installed Fedora a couple of years ago, so GRUB was probably still hanging around from that.  I had long ago set Windows as the default value, so I had forgotten about it until now.  Thanks for the info on restoring the MBR.

---

### Post by confused57 on 2007-06-07
> **Bullfrog245 said:**
> I saw no progress bar or anything.  I had installed Fedora a couple of years ago, so GRUB was probably still hanging around from that.  I had long ago set Windows as the default value, so I had forgotten about it until now.  Thanks for the info on restoring the MBR.

I don't know if this will help, but your bios might have an option for "USB Legacy" that you might want to try.

---

