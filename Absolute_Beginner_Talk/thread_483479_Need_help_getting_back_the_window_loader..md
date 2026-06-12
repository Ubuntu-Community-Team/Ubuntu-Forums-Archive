---
title: "Need help getting back the window loader."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by G-Diggers on 2007-06-24
Hi 
I tried to do a USB install of Ubuntu 7.04 but did something wrong.
The install did go to the USB drive but when I restart and need to go to windows the PC will not start unless the USB drive is installed. What I need is the get the windows xp back to start as normal and want to have the pc look for the USB Drive then load. So the first problem is fixing the Windows loader. Is this possible? This is my daughters PC and she will be upset when she gets back next week. I saw this in the forum before I tried to start this project but can’t seem to find it now. Any help will be appreciated

Thanks in advance

---

### Post by h0ax on 2007-06-24
Ubuntu probably installed GRUB to the MBR of the hard drive -- I'm assuming here, but is that what loads first? "Grub Loading... Loading Stage 1.5... etc" when you have the device inserted?

If that's the case you just need to overwrite the MBR(Master Boot Record) with a Windows installation disk.  Try forum and/or google searching for that.

---

### Post by Clay_Banger on 2007-06-24
to reinstall the windows boot loader, boot into a windows 98 startup disk and enter this command:
```
fdisk /mbr
```
then reboot your machine, it should load into windows.

if you dont have a windows 98 startup disk, you can download one from [here]("http://files.frashii.com/~bootdisk/newjersey/boot98se.exe").

---

### Post by BobCFC on 2007-06-24
If you have the XP cd you can use the recovery console to restore the MBR. Boot it up to blue screen as if you were installing windows and at the welcome screen press R to repair.

Once at the recovery console use the command FIXMBR to restore the master boot record. This will remove grub and just boot the ntbootloader off the C: drive.


EDIT: This has the same effect as the Win98 Startup disk but you may not be able to find one.  Hell I don't have a floppy drive lol

---

### Post by logos34 on 2007-06-24
> This is my daughters PC and she will be upset when she gets back next week.

LOL! Sorry, couldn't resist.  It's usually the other way round--kids messing with dad's pc and totally borking it.

Ooooo are you gonna get it when your...your daughter gets home! ;-)

Seriously, either of the above suggestions WILL work.  Then comes the fun part: installing grub to the external usb and editing boot files so that you can get into ubuntu.

Hurry, you only have...6 days!

---

### Post by G-Diggers on 2007-06-24
I don’t have a Floppy so I tried the XP cd and that fixed it!:p:p
Works Like a new one. Man!! am I glad now I won’t get a beating when my daughter gets back from camp. Thanks For All of the Help and Ribbing. I was wondering if anyone would catch that.:popcorn:
Thanks
:KS:KS:KS

---

