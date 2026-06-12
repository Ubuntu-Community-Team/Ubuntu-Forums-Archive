---
title: "Cannot boot into install CD"
date: 2007-12-15
forum: Apple PPC Users
---

### Post by penguindevil on 2007-12-15
I am trying to install Linux on my computer and I am making no progress. I have made CD-roms of Ubuntu 7.04 Alternate PPC, Ubuntu 7.04 Desktop PPC and Fedora Live 8 PPC. Each of these I had made sure to have burned the Disc Images to the CD's, instead of just putting the contents of the DMG on the CD, or just putting the DMG itself on the cd.. 

The trouble is getting booted. The "hold C" angle, does nothing... If I try holding Option, I do get the Boot Manager with the OSX disc and the "CD with Penguin", but if I click on the Linux disc and proceed, all I get is a black screen and returned to the Boot Manager.

I have tried going into Openfirmware and using the boot command to direct it to the yaboot file on the CD-rom, when I do that, I get a few lines of text that go by too quickly to read and then a gray screen with a circle with a line through it. At this point, the computer needs to be manually restarted.

These are the results with all three of these CD's. Any idea what I am doing wrong? Is there someway that I can install one of these without having to first boot into something other than osx?

I am using a 1Ghz, G4 "mirrored-door", with 512 MB ram, OS 10.4.10 installed on one internal harddrive and a second 55 GB internal harddrive that is empty, and a dvd-ram drive that is not the original...

---

### Post by Washer on 2007-12-16
nvm you're 7.04 I was thinking 7.10

---

### Post by ProgramASPnet on 2007-12-17
Make sure your CD/DVD Drive is connected to the internal ATA33 port on the motherboard.  I do not believe it will boot on the ATA66 port.  This goes for any bootable media I've tried (OS X, Ubuntu, etc) on my MDD system.

---

### Post by albertone on 2007-12-17
I lived the same experience few days ago.
[http://ubuntuforums.org/showthread.php?t=634396]("http://ubuntuforums.org/showthread.php?t=634396")
I thought i will become crazy, and I changed the CD/DVD drive 
It was "just" that !!!!
I hope it's help

sorry for my bad english !

---

