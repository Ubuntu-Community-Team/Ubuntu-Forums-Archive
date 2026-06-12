---
title: "Problem burning CD in Gnomebaker"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by nandog on 2006-08-20
Hello I had a problem burning an audio cd with gnomebaker. I dont understand what the problme is.. thanks for the help. here is the error i get:


cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.33
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identifikation : 'DVD_RW ND-3540A '
Revision       : '1.01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1343488 = 1312 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 0E 58 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.006s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 8636544 bytes
Writing  time:   27.389s
Average write speed 413.4x.
Min drive buffer fill was 30%
Fixating...
Fixating time:   25.019s
cdrecord: fifo had 200 puts and 137 gets.
cdrecord: fifo was 3 times empty and 6 times full, min fill was 0%.

---

### Post by pollock.tar.gz on 2006-08-20
have you tried downloading the newest version of gnomebaker?

---

