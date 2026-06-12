---
title: "burning cds"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-06-18
whenever i try to burn a disc using gnomebaker i get this message

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-28-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'IDE-CD  '
Identifikation : 'R/RW 12x8x32    '
Revision       : 'N3.8'
Device seems to be: Generic mmc CD-RW.
Current: 0x0000
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
Drive buf size : 3244032 = 3168 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Success. read disk info: scsi sendcmd: no error
CDB:  51 00 00 00 00 00 00 00 04 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 4
cmd finished after 0.001s timeout 240s
cdrecord: Cannot get disk type.
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
cdrecord: WARNING: Data may not fit on standard 74min disk.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 60s
cdrecord: OPC failed.
Writing  time:    0.062s
Average write speed 999.0x.
Fixating...
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.001s timeout 240s
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
cdrecord: Cannot get next writable address.
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 480s
cmd finished after 0.001s timeout 480s
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 13 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s


any ideas?

I cant use k3b either, because i get this

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-k7
Devices
-----------------------
_NEC DVD-ROM DV-5800A 1.42 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

IDE-CD R/RW 12x8x32 N3.8 (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [TAO; RAW; RAW/R16; RAW/R96R]


serpentine i get

Insert rewritable or blank disc

nautilus i get

Please put a disc, with at least 114 MiB free, into the drive. The following disc types are supported:
CD-R, CD-RW:popcorn::popcorn:

---

### Post by maitresse on 2007-06-18
please! Anyone?!!!

I have been trawling through all these pages looking for an answer, but getting nowhere fast!! 

Help a noobie today, and do a good deed!! lol

---

### Post by Brightbelt on 2007-06-18
Hi,
I'm not an expert but I can't help but think you've got a hardware conflict, especially considering these lines:

```
cdrecord: Warning: Running on Linux-2.6.15-28-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
```

Either that or the driver is not up to date. You might try Googling the CD-RW for a Linux/Debian driver and see what comes up. 

Another possibility could incompatible media. Have you tried a different brand of CD-Rs?

I'm just trying to put some ideas out there for you. Good Luck,

Frank B.

---

### Post by maitresse on 2007-06-18
tried loads of different cds so it is not that.

i am just totally stumped!

---

### Post by maitresse on 2007-06-18
i can play things through the drive, but it will just not work when i try to record for some reason!

---

### Post by Gwasanaethau on 2007-06-18
I had problems of this form before, and it wasn't writing in Windows either. Do you have Windows installed? If so try a test run there (you'll use up a CD, though) and see. If it doesn't work there either, your 'writing laser' in your CD writer might not be functioning (that's what happened to me). I had to replace the drive when it happened to me (€50/£35/$60 from a good computer store).

---

### Post by maitresse on 2007-06-18
I dont have windows installed so i cant try that

is there nothing in all that stuff i have posted that can tell anyone if there is a system problem?!

---

### Post by Golyadkin on 2007-06-18
Okay, I googled for 10 seconds and found an answer to someone with the same problem:
> 
Let me answer my own question: it turned out that it was a driver problem.
Solution: K3b configure -> Devices -> Cdrdao driver. Change "auto" to one of
the supported drivers ([http://cdrecord.berlios.de/old/private/cdrecord.html](http://cdrecord.berlios.de/old/private/cdrecord.html)).
For my config (see below) "plextor" works fine.
I haven't had similar config problem before updates.


Source : [http://ubuntuforums.org/showthread.php?t=192882](http://ubuntuforums.org/showthread.php?t=192882)

---

### Post by stoodleysnow on 2007-06-18
Are you sitting comfortably?:popcorn:
(takes a deep breath)
If you manage to rule out any software problems:
Make sure the cables (IDE, power) are connected properly to the backs of your optical drives and the jumpers are set as Master to the ROM drive and Slave to the RW drive. Make sure the IDE cable is plugged in with the end (master) connector in the ROM drive and the middle (Slave) cable in the RW drive, using the two connectors which are closest to each other for your drives and the other one for connection into the motherboard. Furthermore, are the connectors the right way up? on the drives the red wire always goes nearest the power cable, and on the motherboard it goes to pin 1 (thick white mark under the socket plastic)
If this doesn't solve it, there can only be the BIOS (ensure it detects them both), the PSU (if it makes high pitch noises that only young kids and animals can hear, stop using it and get a new one) and the motherboard's capacitors (if they are oozing brown stuff from top or bottom OR even if they are bulging, get the motherboard re-capped or buy a new one). If none of these problems exist or if fixing them does not solve the problem, replace the optical drives.:redface:
:)

---

### Post by maitresse on 2007-06-18
> **Golyadkin said:**
> Okay, I googled for 10 seconds and found an answer to someone with the same problem:


Source : [http://ubuntuforums.org/showthread.php?t=192882](http://ubuntuforums.org/showthread.php?t=192882)

Thanks, but i dont understand what i am supposed to be doing!

---

### Post by Gwasanaethau on 2007-06-18
Sorry - no longer needed - superseded by a simultaneous post.

---

### Post by maitresse on 2007-06-18
I have looked at the other post, but it doesnt tell me what to do.  Can someone give me a step by step instruction on this please!

---

### Post by maitresse on 2007-06-18
i really need some step by step instruction here! please peoples!!!:(

---

### Post by Gwasanaethau on 2007-06-18
> **maitresse said:**
> I have looked at the other post, but it doesnt tell me what to do.  Can someone give me a step by step instruction on this please!

Sorry, I meant the one by 'stoodleysnow'. I'd written a long post which basically said some (but not all) of what 'stoodleysnow' said. I'd probably follow his advice, it sounds like the best option. In case you haven't been inside your computer before - be careful. Make sure you're earthed and don't touch any of the chips/electronic contacts, etc. as static discharges can damage them.

It sounds like a hardware problem because all four of the burner programmes fail to detect your disc as a (re-)writeable disc.

---

### Post by maitresse on 2007-06-18
> **Gwasanaethau said:**
> Sorry, I meant the one by 'stoodleysnow'. I'd written a long post which basically said some (but not all) of what 'stoodleysnow' said. I'd probably follow his advice, it sounds like the best option. In case you haven't been inside your computer before - be careful. Make sure you're earthed and don't touch any of the chips/electronic contacts, etc. as static discharges can damage them.

It sounds like a hardware problem because all four of the burner programmes fail to detect your disc as a (re-)writeable disc.

Thanks!  I didnt realise it might mean opening the computer!!!  I think i had better leave well alone! lol

---

### Post by Gwasanaethau on 2007-06-18
> **maitresse said:**
> Thanks!  I didnt realise it might mean opening the computer!!!  I think i had better leave well alone! lol

Lol - fair enough, I'm pretty much the same - scared witless that I'm going to break something! It isn't too difficult, but if you don't feel confident enough then it's better to be safe than sorry! You can always take it to a computer shop where they'll have a look too, for a few quid of course! ;)

---

