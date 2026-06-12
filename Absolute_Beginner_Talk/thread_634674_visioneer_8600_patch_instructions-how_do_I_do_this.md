---
title: "visioneer 8600 patch instructions-how do I do this?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by rolypolycat on 2007-12-08
Hello!

I have a visioneer 8600 scanner. For some weird reason, the gimp seems to think my ATI tv card is a scanner; it can't fine the real scanner. I hunted the forums for help, and found this site and a patch. I'm not sure what I'm supposed to do with this, though. Here are the instructions:

Kernel 2.2.16 with usb backport
SANE 1.0.3

0. Creating device file for your scanner
   mknod /dev/usb/scanner0 c 180 48
   chmod 666 /dev/usb/scanner0
   Or 
   you can visit Karl Heinz Kremer's website
   [http://www.freecolormanagement.com/sane/usb_scanner.html](http://www.freecolormanagement.com/sane/usb_scanner.html)
   for more detailed reference about usb scanner.
1. Uncompress ot.tar.gz to the backend directory, 
   Note there also include a Makefile, please rename
   your own Makefile first, then following operations
   are same: 
   make
   make install
2. copy e1.ini & lut.plg to where the xsane is
3. copy scanner.c & scanner.h to the kernel.
   for example, the 2.2.16 usb backport should be
   /usr/src/linux-2.2.16/driver/usb
4. Build kernel modules:
   make modules
5. the scanner.o should be in the place:
   /lib/modules/2.2.16/usb
6. Insert module
   insmod scanner.o vendor=0x04a7 product=0x0331

Now, you can run the xsane

Am I supposed to recompile my kernal? Is this something a newbie should even be doing? or is there some other way to get my scanner programs to actualy recognize the scanner, not the ATI tv card? I'm using Feisty with the XFCE desktop.
Any help anyone can give me is greatly appreciated. Thanks!

---

