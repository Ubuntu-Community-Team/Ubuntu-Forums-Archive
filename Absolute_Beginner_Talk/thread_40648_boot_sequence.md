---
title: "boot sequence"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by clumsy1007 on 2005-06-09
Hi,

I've finally decided to make the switch to Linux so I dowloaded 5.04 and burned the iso to an image cd.

Now I tested this cd on another computer, and it worked, so the CD should be good. The problem is, the computer I want to install on is really old --- so old that the BIOS doesn't seem to support booting from CD-ROM. When I press F1 to enter setup, I have only four options for the boot sequence:

A: then C: (what I have selected)
C: then A:
A: only
C: only

But I want to boot from CD! Is there a way to do this? The computer is way too slow to run Windows, and I want to toy with Ubuntu.

More about the computer... (if needed)

It's running Windows 98 SE at 90 MHz (not a typo, I don't mean 900MHz) with the original 1GB master hard drive and a 5GB slave hard drive that I added long ago. It's got the original floppy drive and the CD-RW drive I added. Everything works in Windows so I know the hardware is functioning. 

Thanks in advance for your help!

---

### Post by kvidell on 2005-06-09
[http://www.bcdwb.de/bcdw/bcdl_e.htm](http://www.bcdwb.de/bcdw/bcdl_e.htm)
Since oyu have a windows install, it might be worth it to give that a shot.
I tried to find a way to do a grub floppy and throw control to a CD from that, but it apparently isn't posisble.

Hope that helps!
- Kev

---

### Post by wvslkr on 2005-06-09
Smart Boot Manager will allow you to boot from floppy and then to CD.
How much ram do you have?  If it is low you will get no joy.  Old machines need plenty of ram for linux especially if you want to run a Gui.

GL :)

---

### Post by christooss on 2005-06-11
rawwrite will do that to.

[http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)

But... if you have only those options for boot order you have only pentium I. Is that true?

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=clumsy1007]The computer is way too slow to run Windows, and I want to toy with Ubuntu.[/QUOTE]

Let me be honest:

This computer is WAY to slow for Ubuntu as well. Try Damn Small Linux or Feather Linux. Ubuntu is made for modern computers that want the nicest Linux desktop possible, it is not good for reviving machines that won't run Windows.

Honestly the full Ubuntu install wants 128mb of ram and 300mhz before it will work worth using. Either plain Debian or damn small is your best bet- and both might not be able to do more than allow it to be a good nongraphical server.

---

### Post by clumsy1007 on 2005-06-12
Thanks for all the prompt repies! But I'm still having trouble...

For the Bootable CD Loader, I couldn't understand what it was I needed to download or what to do with it. I thought I needed the [zip file from the Bootable CD Loader web page](http://www.bcdwb.de/bcdw/index_e.htm) but then I didn't know what to do with a *.ima file. Am I supposed to burn an image to a floppy drive like i did the *.iso files to the CD drive?

For Smart Boot Manager, I copied the two files (cwsdpmi and sbminst) to a floppy drive, and tried to boot from that, but the computer said disk i/o error. So I then formatted the floppy to a bootable ms-dos floppy and added the two files after the fact - and still got the same error.

Finally, I tried RawWrite. I downoaded and unzipped the installation file (verzion 0.4). But when I tried to boot from the floppy, I got the same disk i/o error.

Am I somehow booting from the floppy wrong? I have bios set to boot from a: first, then c: (remember, d: is not an option). So after checking memory (96 mb, by the way), the computer recognizes the floppy drive then gives me the error.

Again, I'm trying to install linux from a cd on a computer that can only boot from the hard drive or a floppy drive. Your help is greatly appreciated!

---

### Post by wvslkr on 2005-06-12
Try this [http://www.ubuntulinux.org/wiki/SmartBootManagerHowto](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto) should answer your questions :)

---

