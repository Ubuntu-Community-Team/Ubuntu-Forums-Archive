---
title: "Going Around in Circles with GRUB and Drive recognition"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Rochcom on 2006-06-20
I set up a dual boot system with Windows XP Pro. Installed Ubuntu on second physcial drive and GRUB on that same drive.  When BIOS is pointed to that drive, GRUB loads, but gives error messages for either operating system.  Reinstalled Ubuntu and this time put GRUB on BOTH the second hard drive AND a floppy. Both operating systems boot fine from the floppy.  

So, I want to copy the working boot commands in the menu.lst file from the floppy to the hard drive.  BUT, when in Ubuntu, the floppy drive appears in the System folder but will not mount. I tried mounting from the command line (using instructions from another area of this forum) -- the instruction appears to execute yet the drive still does not mount. I tried booting from a Live CD-ROM, but then the floppy does not appear in the System folder or on the desktop, although it does appear in the device manager. 

The system recognizes an external USB hard drive (I don't want to boot from there because it is not always connected) but does not recognize the first hard drive on which Windows is installed (although it too appears in the device manager). 

How can I get Ubuntu to recognize the floppy so that I can read the file?

Can the Ubuntu recognize the Windows FAT32 drive?

---

### Post by richbarna on 2006-06-20
Hi Rochcom, this is THE best page for dual booting info and problem solving :-
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

If you scroll down the page you will see info on GRUB, MBR etc.

Hope it helps ;)

---

### Post by kanem on 2006-06-20
I don't know much about floppies (did you try mounting with 'sudo'?), but Ubuntu can and should recognize your fat32 drive. 

In regards to the GRUB problem: a grub installation needs two pieces of info: which hard drive to install to and where to look for the menu.lst. There are several ways the GRUB installation could screw up. Especially when dealing with multiple hard drives. With a floppy, I imagine it's hard to get wrong; everything goes to the same partition on the floppy.

So, it could be that your menu.lst on your hard drive is wrong as you suspect. Or it could be that GRUB is just looking in the wrong place for it.

If you boot into Ubuntu and post your menu.lst and hard drive configuration in this thread (specifically which harddrive and partition your Ubuntu root filesystem is on) someone here, possibly me, could tell you how to edit your menu.lst and/or re-install GRUB correctly.

---

### Post by Rochcom on 2006-06-27
Thanks for the information.  It should help.

---

