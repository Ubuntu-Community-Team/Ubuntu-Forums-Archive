---
title: "Gnomebaker driving me insane!!"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-16
Hi people - what is going ON??!.

I have Edgy Eft kno3 installed and I am trying.... TRYING to burn a cd iso with Gnomebaker but it fails again and again with this:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW DVR-K16RS'
Revision       : '1.35'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0012 
Profile: 0x0002 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 02 2E 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 05 00 00 09 32 0E 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, deferred error, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 2354 (valid) 
resid: 63488
cmd finished after 0.000s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 1142784 bytes
Writing  time:   20.891s
Average write speed 505.1x.
Fixating...

```

---

### Post by grim918 on 2006-10-16
I am not using Edgy Eft so there could be a problem with it since its still in beta. In the previous releases you can just right click your iso image file and then click on write to disc. That should burn the iso image to the disc. You should give it a try in Edgy Eft.

---

### Post by unlokia on 2006-10-16
Hey thanks but I took the best path of all - stuff Gnomebaker, I installed K3B and now Im rockin!!! :D

MD5SUMS all ok - must be a bug as you said.

Thanks!.

---

### Post by Albi on 2006-10-16
try
sudo gnomebaker

in a terminal

---

### Post by unlokia on 2006-10-16
> try
sudo gnomebaker

in a terminal

Yeah I was just doing that, but halfway, the thought of wasting ANOTHER CD-R (Sony - no errors EVER!) made me install K3B - mucccch better!!!

Methinks ALL Linux cd/dvd writing GUI etc need SERIOUS attention - hey it can't be too hard if closed *cough* Nero *cough* source are doing it right!

---

### Post by Jallu59 on 2006-10-17
There was a bug in gnomebaker 0.6.0.unbuntu1. Now (yesterday, monday 16th of October) they have released 0.6.0.ubuntu2, in which the bug is announced to have been repaired. I haven´t tested yet. My patch was to force the previous version 0.5.x.x to use (forcing can be found in some of Synaptic:s menus).

Yours

Jallu59
an elder ICTpro, but a linux newbie(9 months)

---

### Post by Perfect Storm on 2006-10-17
> **unlokia said:**
> Yeah I was just doing that, but halfway, the thought of wasting ANOTHER CD-R (Sony - no errors EVER!) made me install K3B - mucccch better!!!

Methinks ALL Linux cd/dvd writing GUI etc need SERIOUS attention - hey it can't be too hard if closed *cough* Nero *cough* source are doing it right!

You can get Nero for Linux.

---

### Post by unlokia on 2006-10-17
> You can get Nero for Linux.

:o shame upon you, prophet of closed-sourcedness!!! lol :mrgreen:

I think I would rather use K3B if it's all the same to you - read my numerous closed-source rantings lol

---

### Post by Perfect Storm on 2006-10-17
> **unlokia said:**
> :o shame upon you, prophet of closed-sourcedness!!! lol :mrgreen:

I think I would rather use K3B if it's all the same to you - read my numerous closed-source rantings lol

Well I don't mind close-sources on linux as long as there's open source counterparts :)

But I've my fetish's too. If it require QT libs/or KDE libs it will  not touch my HDD. The good thing is that in Linux we have choices to make :)

---

### Post by ahaslam on 2006-10-17
I just had the same problem on Dapper using backports.

I found that this worked perfectly:
[B]
sudo chmod +s /usr/bin/gnomebaker[/B]


Tony.

---

### Post by merlyn on 2006-10-18
I have experienced a slightly different problem with Gnomebaker 0.6.0 (backport), though in keeping with the title of the thread it drives me insane.

For some reason when I attempt to erase a rewritable cd, it asks me to place a disk in my DVD drive which is read only. This is despite the fact that the correct device, (my Sony CD burner), is displayed in the device drop down menu.

While I'm at it whats with the removal of the 'toolbar', and placing all the icons in tools menu. This irks me as it now takes two clicks to access useful tools.

What irks me even more is there is no option to view this, honestly as much as I love GNOME, this simplification of the desktop based on 'sensible defaults', so as not to confuse the user, is taken way too far at times.

The 'solution' that I have come up with is to install the earlier version, which isn't really a solution at all.

Cheers.

---

### Post by dvarsam on 2006-11-14
> **unlokia said:**
> :o shame upon you, prophet of closed-sourcedness!!! lol :mrgreen:

I think I would rather use K3B if it's all the same to you - read my numerous closed-source rantings lol

I am following the "Artificial's Intelligence" way!!!

Unless K3b, Gnomebaker, and all other Open Source solutions improve, there is only one way to solve this & that is:

nerolinux

Fullstop!

---

### Post by Marquis_de_Carabas on 2006-11-22
> **dvarsam said:**
> Unless K3b, Gnomebaker, and all other Open Source solutions improve, there is only one way to solve this & that is:

nerolinux

Fullstop!

Have you used it? Every review I've seen says that it sucks, and K3b is infinitely superior...

---

