---
title: "[SOLVED] Ubuntu install problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by bvd06 on 2008-01-24
Hi folks, Newbie to the forum and its been sometime since I have done anything with Linux.

I had a new machine delivered to me and I am having touble getting anything loaded on it. Hardware is:
MB - Gigabyte GA-P35-DS3L
Itel Core 2 Duo
4 GB RAM 
160 GB SATA HD (no O/S on it, I presume its unformatted)
LG CD ROM
video - Gigabyte GeForce 7200 GS 

Symptom:
When trying to run up an ISO distro the machine gets to the "Boot from CD/DVD:" with the cursor sitting under neath blinking rapidly. Activity to the CD ROM stops.

I have:
- ensured that hash sums match the distro's i have tried.
- tried 7.10 server and desktop 64 bit versions, 7.10 32 bit server version, a Fedora 64 bit server version.
- I have run up an old copy of Windows 2K and it puts up the loading splash screen and looks like its loading properly.
- I have copied the .iso distro's onto a USB flash drive and set the bios to boot off a USB-ZIP. The hang is the same without the message "Boot from CD/DVD:" coming up.
-have done a lot of googling looking for something similar without much success. Motherboard web site no longer has anything on Linux.

Not sure if I have a compatibility issue or whether I am missing something very fundamental... Any help is appreciated.

---

### Post by gvartser on 2008-01-24
Go into BIOS and check if the floppy is enabled. If it is, then disable it.

Then boot into ubuntu again.

/G

---

### Post by bvd06 on 2008-01-24
Thx for the very quick reply. 
the FD is NOT enabled in the bios.

---

### Post by gvartser on 2008-01-24
Oki that was a long shot..

I read somewhere that there was a similair problem as you have. And that did it.

/g

---

### Post by bvd06 on 2008-01-24
OK, thanks folks I figured it out. I suspect this is probably pretty basic.  Apparently there is a difference between burning an image and burning a data cd. Burning an image was not an option my very old CD burning program supported. I downloaded a program called 'burn4free' that did support this. 

So in summary when creating an ISO disk you can not create the CD by writing to it as a data disk, you must use an application that supports a 'burn image', or 'burn ISO image'.

---

