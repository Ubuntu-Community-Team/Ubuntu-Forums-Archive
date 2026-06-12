---
title: "I want to know a bit more about Dual Booting process..."
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Zero Ziat on 2007-04-07
Yo. I've tested Ubuntu on the Live CD. Although it looked bootylicious, I need to install it so I can start making permanent changes to make my wireless work.

Moving into the topic, what happens is this:

_**Situation**_
I have Windows XP Professional installed.
I want to install Ubuntu, but I cannot backup anything at since I have nowhere to do so.
I have no XP install disc. (**!**)
I verified the Live CD it is not corrupted with the "Check for defects on the Live CD" option in the boot menu. 
I ran a tool in XP that told me that my disk is healthy.
Free Space: 10 Gigs or so on a 40 GB disk.

_**Them Specs**_

**Processor(s)**
Number of processors	1
Number of cores	1 per processor
Number of threads	1 (max 1) per processor
Name	AMD Duron
Code Name	Applebred
Specification	Turbo 3000+
Technology	0.13 um
Core Speed	1593.6 MHz

**Chipset & Memory**
Northbridge	VIA KM400 rev. 00
Southbridge	VIA VT8235 rev. 00
Graphic Interface	AGP
AGP Revision	2.0
AGP Transfer Rate	4x
AGP Side Band Addressing	supported, enabled
Memory Type	DDR
Memory Size	512 MBytes (Which gets reduced to 496 or so.)
Memory Frequency	166.1 MHz (FSB + 33 MHz)
DRAM Interleave	4-way
CAS# Latency (tCL)	2.5 clocks
RAS# to CAS# (tRDC)	5 clocks
RAS# Precharge (tRP)	3 clocks
Cycle Time (tRAS)	7 clocks

**System**
System Manufacturer	VIA Technologies, Inc.
System Name	KM266APro-835
System S/N	 
Mainboard Vendor	 
Mainboard Model	KM266APro-835
BIOS Vendor	Phoenix Technologies, LTD
BIOS Version	6.00 PG
BIOS Date	04/26/2004
Filesystem     NTFS
------------------------------------------------------------------------------------
If you want EVEN MORE info: 

((EXTENSIVE))

[http://zeroziat.uni.cc/GENERAL%20INFO.htm](http://zeroziat.uni.cc/GENERAL%20INFO.htm)

---

### Post by Zero Ziat on 2007-04-07
Hmm... Also, what are the chances of failing?

EDIT: I also remember one time I was just curious and started going through the install until the partition thingy:
I just clicked next on the partition thingy, cursor gone into "Processing" mode and nothing else.
A whole time doing that.

---

### Post by igknighted on 2007-04-07
Well, 10gb is doable if you are willing to give all (or at least most... anything less than 6 or 7 gb, plus another gb for swap will lead to issues) of that space to Ubuntu.  However, then you would be out of HD space just about.

I would suggest (as long as this isn't a laptop, and judging by the chipset I don't think it is) I would travel down to your local computer store and see if they have any old HDs lying around.  The other day I got a 10gb drive for like 6 bucks (used of course).  This is ideal, then you plop that in and unplug the windows drive.  Install Ubuntu, and let it set up the bootloader (called grub) as it wants to.  Then once it is done, re-plug in the windows drive, but specify in your bios to boot from the drive with Ubuntu on it.

NOTE: at this point, linux will not give you the option to boot to windows.  Once you have gotten this far, post back and get instructions for enabling that.  We could have left the windows disk plugged in during install and it would have set this up automatically, but you then run the risk of overwriting the windows bootloader... not a problem if you stick with linux, but if you decide its not for you then you will have a hell of a time restoring the windows MBR without the windows disk.

For now, if you want to boot back into windows, you have to manually choose that drive in the bios.  Once you configure the Ubuntu bootloader (grub), however later once grub is configured you can just boot to grub and have the option there to select either OS from a menu at boot.  If you want more info, check out: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and the Ubuntu wiki (tons of good info here, just browse around... all your questions answered)

---

### Post by Zero Ziat on 2007-04-07
I have about $44 dollars saved from throughout most of my life. (13 years.)
So, I guess I'll bike my way to TecSys and see what I can get. =)

*Smacks Forehead* DUMB ME. Today is 4 AM. When I wake up at about 14 or 12, the store would be closed... I mean, it is saturday. =S

---

### Post by siciliancasanova on 2007-04-07
Like the post above, I would go to the psychocats page to read up on partitioning.  I just did a dual boot with xp pro about 20 min ago.  I would suggest using the [gparted live cd]("http://gparted.sourceforge.net/") to set up your partitions instead of the ubuntu live cd.  They both do the same thing, except when you get errors with the ubuntu cd you won't be able to see them.  If you use the gparted live cd it will display all the errors it found in trying to partition so you know what to fix.

For example, gparted live told me that I shut down XP wrong and it couldn't partition until I restarted it.  This is something the Ubuntu live cd did not tell me, and I could not isolate my problem.

---

