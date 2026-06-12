---
title: "cd burning"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by matpark01 on 2005-08-19
I've just added a CDRW to the system The device is detected and mounts. When I try and burn a cd (using nautilus, gnomebaker, graveman) the device is found (standard ATAPI ) but the burn process just hangs often meaning I need to reboot to get the system going agin. No information is burned on to the CDR
I know cd burning is well covered in other threads but none of solutions suggested seems to work for me!

---

### Post by KingBahamut on 2005-08-19
Does Gnomebaker or K3b supply a detailed output?

---

### Post by matpark01 on 2005-08-19
Thanks. Yes this sort of thing

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Success. read buffer: scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x4 (CONDITION MET/GOOD)
resid: 64508
cmd finished after 5.251s timeout 40s
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-RW 48/16/48X '
Revision       : '150C'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x0008 
Profile: 0x0009 (current)
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 4194304 = 4096 KB

---

