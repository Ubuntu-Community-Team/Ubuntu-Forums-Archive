---
title: "Display Problems"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Foustus on 2007-01-03
Hello, Hello, Hello. I am having problems with the display on my laptop using my new 6.10 installation. I am unable to abtain my maximum res of 1280 x 800 and when I open my browser and try to scroll I get a very wavy delayed reaction. What follows are the complete specs of my laptop exept that I have a little over a gig of mem installed. Thanks for the help.

FEATURES
Operating System: Genuine Windows® XP Home Edition
Display: 15.4" WXGA Widescreen (1280 x 800).  Roughly 10% wider then a conventional 15" display, the LM7WZ provides more viewing area for your desktop applications.
Processor: Intel® Celeron® M Processor 350J, 1.30GHz.  Find out more about Execute Disable Bit technology from Intel®.
Memory: 256MB DDRII 533, upgradeable to 2GB
Hard Disk Drive: 40GB SATA.  As the latest storage interface, Serial ATA provides data transfer rates up to 150Mbytes/sec, 50% faster then older Ultra ATA devices.
Optical Drive: DVD-ROM/CD-RW Combo Drive allows viewing of DVDs and listening or creating CDs.
Graphics: S3 Graphics UniChrome&#8482; Pro
Audio: AC'97
Wireless LAN: Built-in 802.11b/g wireless LAN allows connection to a wireless access point or broadband router.
LAN: (1) 10/100 Ethernet
Modem: (1) 56k Fax/Modem
I/O Ports: (1) DB 15-Pin VGA Port, (4) USB, (1) Microphone Port, (1) Headphone Port, (1) PCMCIA II Slot
Pointing Device: 2 Button Glide Pad

Additional Software
CyberLink PowerDVD
CyberLink Power2Go
Windows® Media Player
Norton Internet Security&#8482;

Warranty: One Year Limited
Technical Support: 24 Hour Toll-Free

 
	 
  	

SPECIFICATIONS
Operating System: Genuine Windows® XP Home Edition
Processor: Intel® Celeron® M Processor 350J, 1.30GHz
Front-side Bus: 400MHz
Graphics: S3 Graphics UniChrome Pro Integrated Processor
Audio: AC97 Codec, 5.1 Channel
Memory Slots: (2) DDR II 533 SDRAM
Maximum Memory Expansion: 2 GB
I/O Ports: (1) DB 15-Pin VGA Port, (4) USB, (1) Microphone Port, (1) Headphone Port, (1) PCMCIA II Slot
Communications Port: (1) 56K data/fax modem
LAN: (1) 10/100 Base-T Fast Ethernet
Expandability: (1) PCMCIA Type II
Power Supply: 65 Watt AC-DC Adapter
Battery: Rechargeable Lithium-Ion
Measurements: 14&#8221; (L) x 10.5&#8221; (W) x 1.5&#8221; (H)
Weight: 5.9lbs

P.S. Also having problem with Broadcom wireless connection

---

### Post by Shatrat on 2007-01-03
I believe you need to edit your /etc/X11/xorg.conf (copy this to a backup first because jacking this up is the leading cause of headaches amongst absolute beginners) and in the Device section make sure it says Driver "savage". 

Then you may also need to go down to the Screen section and add "1280x800" to the front of all the the "Modes" lines.

I don't actually have an S3 chipset, so this may or may not work.

P.S.
Here is a guide to getting your wireless connection going.
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by Foustus on 2007-01-03
Thanks for the help but it didnt work. I got an error message about the x server failing to start.

---

### Post by Foustus on 2007-01-03
boy I am really having problems. not only is my display not working when I plug in my headphones into my laptop that where working under windows they dont work at all in Ubuntu.

[SIZE=6]H[/SIZE][SIZE=5]E[/SIZE][SIZE=4]L[/SIZE][SIZE=3]P[/SIZE]!

---

### Post by Shatrat on 2007-01-03
Here is another thread addressing this problem
[http://www.ubuntuforums.org/showthread.php?t=318520](http://www.ubuntuforums.org/showthread.php?t=318520)

You're gonna need to install drivers for your sound as well perhaps.  First you could try messing with the volume control and mixer and make sure nothing is muted or turned down that shouldn't be.
Getting your hardware working will likely involve some reading and searching, dont be squeamish.

---

