---
title: "CD Burning Failure?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by psyphen on 2007-03-28
For some reason CD burning isn't working for me, although the drive functions fine when reading CDs. I've tried gnomebaker, and that fails along with running cdrecord as seen below from the command-line. Anybody know what the problem is? Like it says below, I have a Plextor PX-320A, and burning works fine in my Windows on the other partition.

```
psy@psy-desktop:~/Desktop$ sudo cdrecord -v -eject speed=16 dev=ATA:1,0,0 ubuntu-7.04-beta-server-i386.iso 
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-11-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: 'ATA:1,0,0'
devname: 'ATA'
scsibus: 1 target: 0 lun: 0
Warning: Using badly designed ATAPI via /dev/hd* interface.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: -1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PLEXTOR '
Identifikation : 'CD-R   PX-320A  '
Revision       : '1.04'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0008
Profile: 0x0008 (current)
Profile: 0x0009 
Profile: 0x000A 
Profile: 0x0010 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE VARIREC FORCESPEED SINGLESESSION HIDECDR 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 2064384 = 2016 KB
Drive DMA Speed: 4452 kB/s 25x CD 3x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   483 MB        
Total size:      555 MB (54:59.54) = 247466 sectors
Lout start:      555 MB (55:01/41) = 247466 sectors
cdrecord: Cannot load media.

```

Thanks very much for the help,
~Psyphen

---

### Post by Bias on 2007-03-29
Gnome Baker also fails for me but dragging the files to the cd icon on screen or directory in nautilus then opening the directory in nautilus and choosing burn or wite button (top righish) works ok. This method also alows .iso burning.

---

