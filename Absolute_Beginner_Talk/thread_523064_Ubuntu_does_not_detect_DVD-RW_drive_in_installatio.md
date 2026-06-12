---
title: "Ubuntu does not detect DVD-RW drive in installation process"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Polaris573 on 2007-08-11
When I attempt to install Ubuntu on my computer it sucessfully loads the installation menu. However, when I star the installation process a menu pops up telling me that Ubuntu cannot detect my any CD/DVD drives.  It asks me to load drivers from a floppy drive.  Is there anything I can do?

**Processor:**	LGA 775 Intel E6550 Core2 Duo "Conroe" 2.33Ghz 4MB L2 Cache
**Motherboard:**	MSI Neo2-FR -- Intel P35 Chipset ICH9R Southbridge
**Memory:**	2GB G.Skill DDRII 800
**Video Card:**	320Mb Evga 8800GTS
**Harddisk:**	250GB Seagate 16MB Cache SATAII and 40GB PATA
**CD/DVD Drive:**	Asus D070 DVD Burner
**Sound Card:**	Creative Sound Blaster X-Fi Extreme Music
**PSU:**	OCZ StealthXStream 600 Watt

---

### Post by GMachine_24 on 2007-08-11
Hi:

A floppy drive. How very old school.

So, what version of Ubuntu are you trying to install?

---

### Post by Polaris573 on 2007-08-11
I'm sorry, I completely forgot to add that in.  It's 7.04 AMD64

---

### Post by louieb on 2007-08-11
Yea its weird it will boot to the CD  but it can't find the CD drive to load the operating system. I've seen this on some older like 15 year old PCs. On these old machines I use the boot option** ide=nodma **or just **nodma**.     
Heres some more stuff on getting it to work.
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Polaris573 on 2007-08-11
I tried a few of those additional commands that seemed relevant with no luck.  Is there any way I can copy the install files to another partition on my hard drive and have it read them from there?

---

### Post by louieb on 2007-08-11
This was written for edgy but it should be adaptable to Feisty.
[HOWTO: Install Edgy 6.10 from an .iso file - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316093")

---

### Post by GMachine_24 on 2007-08-22
Hi:

Have you attempted a "live boot"  to see if . . . well, I'm not sure what. But essentially  to see if that works and if the live version will load a driver that words for your optical drive.

And I hate to ask this, but have you tried a different cd/dvd drive? Yours SHOULD work. But sometimes it's not worth all the effort or if you can install Ubuntu from, say, an old CD-ROM drive you can add the DVD drive later and sometimes it works - like magic.

I'm assuming, also - going back to basics - that your BIOS is set so the CD/DVD drive is the first boot device? Sometimes a computer of mine will *decide* to make the network interface the primary boot device and then the computer does nothing - starts to boot, says it cannot find install files, etc.

You might make your first install device your optical drive and then disable all other options (2nd boot device, 3rd boot device, etc.) so your computer has no choice but to use the optical drive. I know this probably seems like a waste of time but when something is usually simple and resists all attempts at a fix it's sometimes best to just go back to square one, even if you think you've been there four times already.

Just some suggestions.

--gm

---

### Post by SenseiJonny on 2007-11-09
I know this thread's a bit old, but I just have to post since my setup is very similar.

I also have MSI's P35-Neo2-FR motherboard, BIOS v1.4.  I'm using the E4400 Core 2 Duo (on MSI's website, it is listed as compatible as of v1.4), with the same G.skill RAM, and an NEC dvd-drive (IDE).  I have a SATA drive and an IDE drive connected as well as an x1950 ati video card.

I have been working on this for days without any progress.  I just wanted to post the things that I have tried so that, eventually someone will figure out the problem.

I have done memtest more times than I care to count.  I am sure it's not the RAM.  I've tried several CD and DVD drives.  I've tried disconnecting the SATA drive, the IDE drive, and even both.  I've tested the hard drives and the dvd drive in another computer and they worked fine.  I've tried disabling various controllers in the BIOS, mainly the USB and On-Board LAN.  I've tried with and without a floppy attached as well.

Now, what have I tried installing?  Well, as far as ubuntu, everything from Dapper to Gutsy (alternative install cd's)--no success.  I've tried installing windows xp, but every disc I have fails at or before where it says "setup is starting windows"--I never make it to the recovery console.  Even my trusty SystemRescueCD fails me.  Again, it cannot mount the CDROM because it says it cannot find it.  By the way, everything I am trying is 32-bit versions.  I haven't tried any 64-bit versions, but the fact that I can't load my SystemRescueCD is troubling in itself.

I've already tried RMA'ing the board for a replacement, but I am having the same issues.  Despite that, I still suspect it is the board (defective by design).

One thing I had wanted to try but couldn't due to lack of availability was to test with a SATA DVD drive.  If anyone has done this (or wants to send me a free SATA DVD drive?), please let me know.  Any other ideas would be much appreciated.  I've been pulling my hair out over this for way too long...

I'm thinking of returning it for an Asus P5K...


EDIT:  I forgot to include a link to [this thread]("http://www.sysresccd.org/forums/viewtopic.php?t=1325") on the SystemRescueCD forums.  The idea of a "linux hostile" mobo is funny, though keep in mind that windows doesn't work either.  Nevertheless, it had some interesting ideas applicable to this situation, despite the hardware being different.

---

