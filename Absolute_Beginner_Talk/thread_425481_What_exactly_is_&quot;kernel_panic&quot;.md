---
title: "What exactly is &quot;kernel panic&quot;?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by maceintn on 2007-04-27
Hello,
OK, here goes:

HP Pav a1113w: 2.93 GH  P4, 1.5 G DDR, BIOS=AMI (latest from HP) 
drive 1=Samsung SP1614C 160GB SATA, drive 2=Maxtor 6L060J3 60GB PATA with SATA adapter, drive 3=Seagate ST380011 USB hard drive 80GB, Lite-on DVDRW SOHW-1633S,  
Communications: 1394 net adapter, Realtek RTL8139/810X Ethernet NIC
Display: Diamond S9250 PCI 256 DDR Adapter, Intel 8291G/GV/910GL mo-bo chipset,two HP monitors, UltraMon Display Mirror Driver
PS/2 keyboard and mouse

On drive 0 I have it partitioned with GRUB for dual boot. This was created with a SUSE ISO about a year ago. SUSE doesn't work, but I'm able to select Win XP home and it works. (me thinks probably for same reason!)

1-burned UBUNTU 7.04 liveCD desktop image using SONIC DigitalMedia+ at 4X
2-set BIOS to boot from DVD first
3-boot to CD:
4-checked CD from UBUNTU menu: it passed
5-started from line one of menu
6-it loads kernel, starts loading drivers, scrolls lines of text, then hangs!(with flashing underscore cursor at bottom of screen)

At this point, I thought I would try to get rid of Grub and the old linux partitions, so I:
1-burned gparted liveCD 
2-booted that:
3-used first option: gparted livecd 0.3.4-6 (auto-config): lines scroll, then hangs
lastline=<0>kernel panic - not synching: attempted to kill init!
***while watching the text go by I noticed two lines that say "didn't find...(can't read, goes by too fast, but one says "Logitek" something!)

OK,,,It seems to me that I need to be able to read that text. How do I do that?
Then, what do I do with that Knowledge?

---

### Post by compiledkernel on 2007-04-27
Black screen of death , instead of blue, and alot easier to recover from. 

A kernel panic is a message displayed by an operating system upon detecting an internal system error from which it cannot recover; the term is largely specific to Unix and Unix-like systems. The kernel routines that handle panics (in AT&T-derived Unix source code, a routine known as panic()) are generally designed to dump debugging information to either the screen or a specified file and then freeze the computer. The information provided is not always useful to the user, but can sometimes provide troubleshooting data for a system developer or tech support personnel. Attempts by the operating system to read an invalid or non-permitted memory address are a common source of kernel panics. A panic may also occur as a result of a hardware failure or a bug in the operating system.

---

### Post by maceintn on 2007-05-11
> **compiledkernel said:**
> Black screen of death , instead of blue, and alot easier to recover from. 

A kernel panic is a message displayed by an operating system upon detecting an internal system error from which it cannot recover; the term is largely specific to Unix and Unix-like systems. The kernel routines that handle panics (in AT&T-derived Unix source code, a routine known as panic()) are _generally designed to dump debugging information to either the screen or a specified file and then freeze the computer._ The information provided is not always useful to the user, but can sometimes provide troubleshooting data for a system developer or tech support personnel. Attempts by the operating system to read an invalid or non-permitted memory address are a common source of kernel panics. A panic may also occur as a result of a hardware failure or a bug in the operating system.

Wellll, let's see. Where did I leave off?! Oh yes, I then burned at 4X the "alternate" version. I booted this...blast, I can't remember what happened

---

