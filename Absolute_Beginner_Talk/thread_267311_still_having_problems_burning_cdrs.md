---
title: "still having problems burning cdrs"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-09-28
Ok....been having this problem ever since install.

Just now getting around to trying to fix it.

For whatever reason I am unable to burn CDRs of any kind.

GnomeBaker returns the following in the terminal during operation.

any help appreciated

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-386
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
Vendor_info    : 'TDK     '
Identifikation : 'CDRW321040X     '
Revision       : 'Df41'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R96R
Drive buf size : 4091904 = 3996 KB
Drive DMA Speed: 14933 kB/s 84x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 30 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!
```

please note i had forgotten to put in a cd at first.....but after one is placed in the drive it still errors out.

---

### Post by bodhi.zazen on 2006-09-28
Try these links:

[[color=blue]How to fix CD burning issues[/color]](http://ubuntuforums.org/showthread.php?t=217472)

---

### Post by CloudyHaze on 2006-09-28
still getting wrong disc/no disc error


```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
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
Vendor_info    : 'TDK     '
Identifikation : 'CDRW321040X     '
Revision       : 'Df41'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R96R
Drive buf size : 4091904 = 3996 KB
Drive DMA Speed: 14796 kB/s 84x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 30 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!
```


tried both issue fixes

---

### Post by bodhi.zazen on 2006-09-28
can you re-boot and then post output of ```
dmesg
```

---

