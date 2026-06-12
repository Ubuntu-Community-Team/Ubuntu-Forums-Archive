---
title: "This one last problem"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Cysman on 2006-01-25
I'm still having a bit of a problem burning a cd.  I've tried Kb3, and Gnomebaker and another program I can't remember off the top of my head.  Looking at this collection of abominable words below, it seems to my uneducated noggin that I may have a permission problem with my cdrw.  I've checked to make sure I was in the user group for the cdrom which I seem to be but when I check properties under the cdrom, it says I'm not the owner and can't change the permissions.  Can someone clue me in.  Be advised, I'm real new still and the use of crayons will be needed.  



cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type : Removable CD-ROM
Version : 0
Response Format: 1
Vendor_info : 'PHILIPS '
Identifikation : 'CDD4851 CD-R/RW '
Revision : 'C3.7'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A 
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
Drive buf size : 3244032 = 3168 KB
Current Secsize: 2048
ATIP info from disk:
Indicated writing power: 5
Reference speed: 2
Is not unrestricted
Is erasable
ATIP start of lead in: -11635 (97:26/65)
ATIP start of lead out: 359849 (79:59/74)
1T speed low: 0 (reserved val 0) 1T speed high: 4
2T speed low: 8 2T speed high: 0 (reserved val 10)
power mult factor: 4 6
recommended erase/write power: 3
A1 values: 02 4C B0
A2 values: 4A C8 36
Disk type: Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Starting to write CD/DVD at speed 4 in real BLANK mode for single session.
Last chance to quit, starting real write in 5 seconds. 4 seconds. 3 seconds. 2 seconds. 1 seconds. 0 seconds. Operation starts.
Performing OPC...
cdrecord: OPC failed.
Blanking entire disk
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB: A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 13 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.907s timeout 9600s
cdrecord: Cannot blank disk, aborting.
Ah fiddlestix

That last part I put in myself

---

### Post by endersshadow on 2006-01-25
Try running it as sudo.  Additionally, you can attempt to run Gnomebaker as sudo by using the following command:

```
gksudo gnomebaker
```

---

