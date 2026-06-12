---
title: "OK, Linux on my powerbook - osx, How do I do it?"
date: 2009-10-19
forum: Apple Hardware Users
---

### Post by Tobias-sama on 2009-10-19
[COLOR="Indigo"]okay, stumbled upon a mac and want to put linux on it, tried putting the disk in and having it just happen, like it does with PCs, it didn't.. so.. yea, I'm out of ideas, how do I wipe my mac OS and put ubuntu on it instead? searched around here for a bit, but I couldn't find a nice comprehensible and very simple thread explaining every step. 

remember, I don't know anything about macs, I had problems putting firefox on it, so be very .. step by step..ish

thanks : P [/COLOR]

---

### Post by Bachstelze on 2009-10-19
Moved to Apple Users.

---

### Post by Ravernomina on 2009-10-21
If you know a PC then this will be simple.

Burn a new Ubuntu PowerPC version.
Turn the Mac On and hold the C key while the CD is in the disk drive
Boot Up into Ubuntu using the Live CD option
Then go into system>admin> Partition tool
Delete the HSF+ and any other partitions (DO NOT DELETE EFI IF THEIR IS ONE)
Then make a New Linux Swap partition (1 gig = 1024 MB)
Then make a EXT4 Partition
apply the changes and go to install
On the keyboard selection change it to USA     USA - Macintosh
On the partition part Mount point should be "/" for EXT4
Give your details
Hit install
Once done Reboot and start checking for what hardware needs support or non-open source drivers


Post back if need anything

---

### Post by Tobias-sama on 2009-10-25
[COLOR="Indigo"]okay, so I located the correct CD image, burnt it, did the c key thing and booted into ubuntu using the live CD option, however for some reason the graphical display is extremely gimped; there are horizontal bars dancing across my screen, however, i believe that other than graphical issues ubuntu booted up fine, because I heard the familiar startup noise and upon pressing enter the horizontal lines changed  color, henceforth so.. yea.. what do I do? 

extra-information: upon trying to open in a different mode i encounter this related sounding and very low graphics error message:

ubuntu is running in low graphics mode

the following error was encountered you may need to update your configuration to solve this 

unable to find a valid framebuffer device
failed to open framebuffer device concult(?)
warning and/or errors above for possible reasons
screens found but none have usable configuration[/COLOR]

---

### Post by eddib on 2009-11-22
> **Tobias-sama said:**
> [COLOR="Indigo"]okay, so I located the correct CD image, burnt it, did the c key thing and booted into ubuntu using the live CD option, however for some reason the graphical display is extremely gimped; there are horizontal bars dancing across my screen, however, i believe that other than graphical issues ubuntu booted up fine, because I heard the familiar startup noise and upon pressing enter the horizontal lines changed  color, henceforth so.. yea.. what do I do? 

extra-information: upon trying to open in a different mode i encounter this related sounding and very low graphics error message:

ubuntu is running in low graphics mode

the following error was encountered you may need to update your configuration to solve this 

unable to find a valid framebuffer device
failed to open framebuffer device concult(?)
warning and/or errors above for possible reasons
screens found but none have usable configuration[/COLOR]

exactly the same problem.

need help

thank you

---

### Post by tiresia on 2009-11-23
Which kind of PowerBook do you have: G4? Which version of Ubuntu are you trying to install? Do you want to keep MacOSX in DualBoot with Ubuntu?

---

