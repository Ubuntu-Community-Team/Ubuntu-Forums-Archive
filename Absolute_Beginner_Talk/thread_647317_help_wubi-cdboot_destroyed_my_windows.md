---
title: "help wubi-cdboot destroyed my windows"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by GOD-CGS- on 2007-12-22
i was in windows looking on the ubuntu disc before starting install on second drive and accidentally double instead of single clicked wubi-cdboot.exe 

this started an install process in windows that could not be cancelled and then rebooted, i took out the unbuntu disc and all i can get now is 

GRUB loading Stage1.5

GRUB loading, please wait...

ERROR 17.

I cannot even get into windows to fix it

How to I get this back to boot windows 

Things i have tried, booted from ubuntu cd & 
1) putting back boot.ini to normal
2) replacing other 2 boot files for generic
3) deleting all ubuntu files off my hard drive

where is the file that forces my pc to boot grub instead of windows ?

i dont have my windows disc with me to run repair because i am away from home for christmas and my laptop id fu@ked. Yes my lappy has got 2 hard drives its an alienware area 51 m7700 

PLEASE HELP

---

### Post by GOD-CGS- on 2007-12-22
Help:(

---

### Post by Sef on 2007-12-22
1) Do not bump up your post until after 24 hours has gone by.   You can receive an infraction for that.

2) Get [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") and reinstall GRUB.

---

### Post by CouchMaster on 2007-12-22
You should have let the install complete - then just deleted the one you didn't want.  After all, it's in a folder...

Find grub and modify - or add - these lines via a terminal; you can use your Ubuntu CD

find out where grub is and type

root (hd0,0)  ****this will be where ever you find grub********
setup (hd0)

then type

title windows
root (hd0,0)
chainloader +1
quit


if you are using Vista you are probably SOL

---

### Post by GOD-CGS- on 2007-12-22
> **Sef said:**
> 1) Do not bump up your post until after 24 hours has gone by.   You can receive an infraction for that.

2) Get [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") and reinstall GRUB.

i dont actually want grub on this harddrive, i just want it to run windows on this one & ubuntu on sedond drive.

---

### Post by GOD-CGS- on 2007-12-22
> **CouchMaster said:**
> You should have let the install complete - then just deleted the one you didn't want.  After all, it's in a folder...

Find grub and modify - or add - these lines via a terminal; you can use your Ubuntu CD

find out where grub is and type

root (hd0,0)  ****this will be where ever you find grub********
setup (hd0)

then type

title windows
root (hd0,0)
chainloader +1
quit


if you are using Vista you are probably SOL

please excuse my noob questions but i am new to linux, do you use terminal when umbuntu desktop has loaded from CD ?   because this says there is an error if you type (hd0,0) and says its expecting `hd0,0'  ??

or is there a way to boot straight into terminal with cd?

---

### Post by rkd on 2007-12-24
If you can borrow a Windows installation CD from someone near your home, that probably would be the simplest solution.  Be sure you borrow a CD for the same version of Windows as you have installed, boot it, choose the recovery console, and use the fixbmr command.  You can find more detailed directions for that by searching the forums for fixmbr.

Some places say the procedure is different for Vista, so if you have Vista, be careful to find Vista-specific directions.

If you can't borrow a Windows install CD, maybe you can get someone to download and burn a copy of the Ultimate Boot CD for Windows (UBCD4wind), from:

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

That has two programs that could solve your problem: mbrfix and MBRwizard.  Descriptions here:

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)
[http://www.mbrwizard.com/reference.shtml](http://www.mbrwizard.com/reference.shtml)

It looks like MBRwizard won't work for Vista, but mbrfix will (but I don't know whether UBCD4win has the most recent version of mbrfix, so be careful).

It might be that the reason you are having trouble fixing the GRUB setup from the live CD is that when you are running from the live CD, the boot environment isn't the hard drive. I once saw some directions about how to adjust things after booting from the live CD so that you could use GRUB to fix things up, but I don't know where to find those directions now.

I hope someone else posts a simpler way to fix your problem, because none of these are really very easy.

---

### Post by rkd on 2007-12-24
I found what might be an easier solution on this page:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It is the Super GRUB Disk, and it has both a way to boot Windows when the MBR is messed up and a way to restore the MBR to boot Windows.  Unfortunately, the web page is very long.  Here are the relevant directions, once you have a Super GRUB Disk to use on your computer:

---------------------------------------------------
Quick Solutions:

I installed GRUB to MBR with a Gnu/Linux distro (dual boot), and Windows no longer boots.

1) I just want to boot Windows for now, I'll fix it later,

 - boot your SGD floppy disk, USB disk or CD-ROM 
 - English Super Grub Disk 
 - Windows 
 - Boot Windows 

This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood. 

2) I  want my MBR pointing to Windows  bootloader again  - right now!

 - boot your SGD floppy disk, USB disk or CD-ROM 
 - English Super Grub Disk 
 - Windows 
 - Fix Boot of Windows 
--------------------------------------------------

You can find those directions about halfway down the very long page.  Just above that point, it has some screen shots of what Super GRUB Disk looks like when it first boots, which would be good to look at.

The part of the web page above that point gives directions for making a Super GRUB Disk in a variety of situations.  

If your computer has a floppy disk drive, I think you would be able to boot the Live CD, download the floppy disk image, and follow the directions at:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

to write it to the floppy.  I imagine the Live CD has everything you need to do that.  

If your computer doesn't have a floppy, perhaps you can still use that approach if you can borrow a USB floppy drive.  Check to see whether your computer can boot from a USB floppy before trying that -- look in the BIOS boot setup to see whether you have that choice.

If the floppy disk approach doesn't work for you, see whether you can get someone to download the CD .iso image and burn it to a CD for you.  The web page has directions for doing it in Win98, WinXP, and Linux.  There are links to each in the big box of links near the top of the page.  Make sure the person burning the CD for you knows the difference between burning an .iso image and burning a data disk.

---

