---
title: "Lots of Bugs &amp; Crashes (PIII / 128Meg with Xubuntu)"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Zipzit on 2007-11-18
This is my first posting in this forum, and in fact my first time attempting to use any Linux package at all.  I've done my research pretty carefully.  This has been an extremely frustrating experience.  This load is extremely buggy... freeze ups, automatic boot ups for no apparent reason.  I often get the freeze where the scroll lock and Caps light blink (I guess you call that a "Kernel Panic" ?)

I'm using Xubuntu alternate load ver 7.10: reference ([http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)) I had a heck of a time doing the install.  I've booted with "noapic  nolapic  acpi-off (yes I know... now... I copied that exactly off a forum post, sigh) irqpoll and ht=on.  ACPI=Off has been fixed.  

Obviously I've got next to no clue what all of these things do, I copied these hints off of other postings on this forum.  I hate doing mindless work.  

Hardware: Intel PentiumIII 500mhz at PC100.  No overclocking or anything.  Memory = 128Meg. Oh... and I did just place a bid in ebay for more memory, thanks for asking.   ABIT-BE6 motherboard, vintage '99/'00 or so.  This did not have the Bios that read past 137gig barrier in hard drive.  I have been using the drive with winXP sp.2, which I think manages the addressing shortfall (I've been using it for almost one year now.)  Not sure how ubuntu deals with this.  Hard drive West.Digital 250Gig, wiped totally clean. (obviously >137 gig).   I used the standard with LVM install. I have not looked at the disk partitions (I guess I could do that easily with Hiren's disk tools.)  I did check the CMOS battery with a volt ohm meter.  It did have good voltage. I didn't check it under load. 

 I also was eventually able to place the DNS server info into the system... (thanks AT&T for screwing up my life on that one... every computer in this house has to be reset with manually configured DNS servers, else no internet access...  Its tough when you have a laptop that you use in work, home, travel.)  

Generally this thing crashes on boot up, or gets me between 90 seconds and 5 minutes of operations, then crashes or freezes up.  On one occasion it zero'd the calendar to Jan 4th, 2000.  I've cleaned that up now.  

I've not been successful doing the initial package for upgrades (never enough time, sigh.) I have always been able to boot to 7.10 recovery mode always, but sometimes that hangs by going to a black screen too.  this thing is baffling and more than buggy for me.  Often the thing will freeze up on the initial graphic flash screen.

As for boot logs:  /var/log/dmesg has 269 lines.  I have to type key stuff here by hand (for obvious reasons..)  I'm using the Pico editor to look at those files (much easier than VI...)  for reference:

          sudo pico /var/log/dmesg

.. ACPI:  Looking for DSDT in initramfs.. error, file /DSDT.aml not found.
Local APIC not detected.  Using dummy APIC emulation.
* Found PM-Timer Bug on chipset.  Due to workarounds for a bug, this clock source is slow.  Consider trying other clock sources
(after big time jump) Marking TSC unstable due to: possible TSC halt in C2.  
Time: acpi_pm clocksource has been installed.
8139cp 0000:00:0f.0: This (id 10ec:8139 rev 10) is not an 8139C compatible chip
8139cp 0000:00:0f.0: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.28
ACPI:  PCI Interrpt Link [LNKA] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered.
ACPI:  PCI Interrupt 0000:00:0f.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
eth0: RealTek RTL8139 at 0xc885a000, 00:60:67:72:bf:11, IRQ 5
eth0: Identified 8139 chip type "RTL-8139B"
Attempting manual resume
swsusp: Resume from Partition 254:1
PM: Checking swsusp image.
PM: Resume from disk failed.  
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds.
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.  

Obviously this isn't the whole thing.. I'm typing this by hand.  

     sudo pico /var/log/syslog

results in 650 lines (big sigh..)  Nothing jumps out at me there.  No error messages. No asterix's.  ditto for 

     sudo pico /var/log/messages

Anybody got a clue what's going on?  Anything else that I should be looking at?  

thanks in advance for any advice.
LB
Detroit.

---

### Post by digifan on 2007-11-18
Try disabling ACPI in the BIOS and and change setting somewhere that enables plug 'n' play os to state you don't have plug and play os. This helped me a lot on older chipsets.

---

### Post by Zipzit on 2007-11-20
I wanted to follow up in case others may be having the same sort of problems.  I think I have this thing mostly fixed now.

I have been working on this thing almost non stop for three or four days now. 

Hints for troubleshooting:
--locate computer where you can easily see the CD  and hard disk led indicators.  (took me a day or two to move my cpu from way under the desk..) This really helps when determining if the system is hung up or not.  There are some processes (in initial upload) that take a very long time.  Its hard to tell if you are processor hung or not?  If the hard drive is blinking, even a little bit, you are still operating.  

--there is a lot of "try this" advice on the web.   Way too much.  I'd be careful before just throwing an unknown command at things.  

--Best is to read the /var/log/syslog    Best tool for that (for me) seems to be

 "sudo nano /var/log/syslog" 

 When the file first opens look at how many lines there are..  This file gets real big.  Use 'CTRL_"    (control underline) to go to the end of the file and work backwards from there. (I was using old skool unix 'pico' but figured out it was just mapping to linux application 'nano'   way more friendly than VI ... yuck!)

My system was extremely unstable, never lasting more that 2 or 5 minutes.  Generally I would go into Kernel panic mode for every failure, including occasions in text mode.  I didn't have a clue on where to look.  Memory test seemed okay.  

--Look at that file for hints on what could be wrong.  For me in this application I found two things disturbing.  One was the error "ACPI: Unable to load the System Description Tables"  work around for me was adding "linux acpi=off" .  Apparently there is a known problem and perhaps a fix (ref: acpi_scan_rsdp() breaks some PC's by not... by TJ, Ubunto Kernel ACPI team, 25 Sept 07)

the other thing that caught my eye in the /var/log/syslog was entries involving clocks and time.  Specific error was "Found PM-Timer Bug on the chipset ...."  I found a posting that described what this meant, kinda sorta ( [http://lkml.org/lkml/2006/11/30/2](http://lkml.org/lkml/2006/11/30/2) )  One of the notes in there was a reference to use 'a different clocksource (the TSC is probably safe, but **not necessarily.** (bold is from me..)   In my syslog was an entry that it was using the TSC as a clock source.  Often in my logs I'd see postings that there was the need for time adjustments (like the system would be off a tenth of a second in ten minutes of operations, etc...  

I also found an entry in ubuntu forums #156771, ref: "Webpage freezes entire system".  The posting was from jorgepeixoto, stating that he solved random crashes by underclocking his system.  My system is a intel brand PIII 500(100) so that was what I had it set on in BIOS.  When I under clocked it to next slower speed, wow.. bingo, eureka, nirvana!  System became totally stable.  Not sure why the 'advertised' speed isn't stable, but that's where I ended up.. I'm running the bios at 500(66) (I don't get a lot of choices)  Who knows, perhaps the 'clean out your cooling system fins of dust and that will fix everything' guys are correct.  could a warm CPU system affect clock stability?  At first glance I hate those kind of recommendations without a 'why' attached to them.  Your mileage may vary.

Anyway, Jorge, you are my hero!!  mucho gracias.


Finally, perhaps you've got some of the same problems as I, and I hope these suggestions help.  An any rate, be consistent, take notes on what you are doing at each step of the way.  Good luck.  I consider this issue solved.  

Zip,
Detroit, Michigan

---

