---
title: "[SOLVED] Help! Erasing a CD-RW with k3b"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-04-14
I downloaded aptoncd recently, and I was going to write the image file to a CD-RW that had previously been used.  It wouldn't write to the CD.  I did some Googling and found k3b would supposedly do a good job of erasing a CD-RW.  I downloaded and installed the program and got this:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4240N E112 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=10 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-11-generic

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4240N'
Revision       : 'E112'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1705200 = 1665 KB
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 1
  Reference speed: 0
  Is not unrestricted
  Is erasable
  Disk sub type: Ultra High speed Rewritable media (2)
  ATIP start of lead in:  -11076 (97:34/24)
  ATIP start of lead out: 336075 (74:43/00)
  1T speed low: 16 1T speed high: 16
  2T speed low:  8 2T speed high: 24
  power mult factor: 4 5
  recommended erase/write power: 1
  A1 values: 66 4A 99
  A2 values: 38 80 00
  A3 values: 04 C4 A0
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Waiting for drive to calm down.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.012s timeout 9600s
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 9600s
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.
Performing OPC...
Blanking PMA, TOC, pregap

What's going on?  I deduced that k3b is a shell for cdrecord, and cdrecord doesn't really like Linux kernels above 2.4.  I also tried the command-line command 

sudo cdrecord blank=all

Alas, that didn't work either. I looked at some of cdrecord's version number, and  it's 2.2 or something like that (see error log for actual version), and it's a clone of cdrecord.  Synaptic says the latest version is 4.5.  Would removing cdrecord and reloading it work?  

Thanks to everyone in advance for your help!

---

### Post by rai4shu2 on 2007-04-14
You sure it failed? I know there's a ton of scary messages, but in the midst of them:

> No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error

---

### Post by zvacet on 2007-04-14
This is last version o K3b
[http://k3b.plainblack.com/k3b-news/k3b-1.0-announcement]("http://k3b.plainblack.com/k3b-news/k3b-1.0-announcement")

---

### Post by lee292 on 2007-04-15
> **rai4shu2 said:**
> You sure it failed? I know there's a ton of scary messages, but in the midst of them:

Yep, it failed.  File browser still shows files on the CD.  Also, near the bottom of the error log is this:

/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.

I re-read the log and found this line:

Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0

The CD in question was formatted in Window$ using Roxio Easy CD Creator in a format that allows one to drag and drop files to the CD, UDMF or something like that, that K3b or cdrecorder doesn't recognize.  I did have success in writing the aptoncd image to a "virgin" CD.  Next time I go shopping, I'll pick up some new CD-RWs, copy some stuff to one and see if K3b can erase them.

---

### Post by dwblas on 2007-04-15
I use burncenter, which is a perl script.  There are two options for erasing, quick erase and blank a CDRW.  Quick erase works for a while, and then you have to use "Blank a CD", which I assume is a format.  You might try a reformat in either MSWIndows or Linux.  Also, I know that MSWindows has several different third party CD read/write programs available, and AFAIK none of them are compatible with each other.  So in the closed software tradition, it seems that each one does something that only it's own software can recognize, locking you in.  You might have to either format it in Linux or be stuck with using the Roxio progam only.

---

### Post by Hraefn on 2007-09-22
Old post, but I've had issues with this same burner, and from what I can tell, it could possibly be an issue with the CD RW/DVD drive itself.  It's a POS put together by Hitachi and LG from early 2000s, and being the unfortunate owner of one, I've had nothing but trouble with it. I'm currently on the hunt for a way to update/upgrade the firmware, if possible, or I might throw down some moolah on eBay for a new one.  It's just sad when the burner doesn't work (esp. when I want to create some nice new images of linux disks).

If anyone can assist me with this hardware issue, I'd be much obliged.

Below is what I get when I put in a known blank CDRW:

hraefn@worker-ant:/usr/bin$ sudo cdrecord blank=all
Password:
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4240N'
Revision       : '0H22'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: CD/DVD-Recorder not ready.
hraefn@worker-ant:/usr/bin$

---

### Post by lee292 on 2007-09-24
I've posted problems with the CD burner on other threads I've started, and the consensus does seem that the burner that Dell put in my machine is pretty crappy.  Maybe it's time to go out and get another one.   Anybody know how to swap them out of Dell's plug in module?

---

### Post by lee292 on 2008-02-15
The problem was in the drive.  Got another one and now it works!  Thanks to all!

---

