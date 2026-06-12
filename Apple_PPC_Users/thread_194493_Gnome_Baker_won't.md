---
title: "Gnome Baker won't"
date: 2006-06-11
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-06-11
It worked fine in Dapper Beta but now Gnome Baker won't burn squat. Here's the output from my attempt to burn an .iso cd:
Thanks for any help.

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-23-powerpc
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (powerpc-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'DVD-R   UJ-815  '
Revision       : 'D0C4'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1343488 = 1312 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: WARNING: Data may not fit on current disk.
cdrecord: Notice: Most recorders cannot write CD's >= 90 minutes.
cdrecord: Notice: Use -ignsize option to allow >= 90 minutes.
cdrecord: Notice: Use -overburn option to write more than the official disk capacity.
cdrecord: Notice: Most CD-writers do overburning only on SAO or RAW mode.

---

### Post by BoneKracker on 2006-06-20
Does the built-in "CD/DVD Creator" work?  How about cdrecord from the terminal?

---

### Post by ubuntubrian on 2006-06-21
No-to be brief. I've never had luck with Nautilus CD/DVD creator

---

### Post by BoneKracker on 2006-06-21
when was the last time you tried it

They all use cdrecord anyway, if I'm not mistaken.  I was just thinking this might help you isolate the fault.

---

