---
title: "help getting CD writer to work"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2006-11-24
Hi,

I'm having trouble getting my cdwriter to work on xubuntu, 
Its an iomega zip cd 650  - it plugs into the USB socket at the back of my computer.
I can mount it and read data cds but when I try to write a CD I get error messages: 

using graveman: 
> usr/bin/mkisofs: No such file or directory. Invalid node - (null)

using xfburner:
> cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
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

TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'IOMEGA  '
Identifikation : 'ZIPCD 650 USB   '
Revision       : 'I1.1'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
cdrecord: Warning: controller creates hard SCSI failure when retrieving CD capabilities page.
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.



in DAO mode the error message is the same except > "Drive does not support **SAO** recording


in raw16 mode the first part of the output is the same then the error message is 

> Driver flags   : 
Supported modes: 
Encoding speed : 132x (9826 sectors/s) for libedc from Heiko Eißfeldt
cdrecord: Input/output error. prevent/allow medium removal: scsi sendcmd: retryable error
CDB:  1E 00 00 00 00 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
cdrecord: Input/output error. start/stop unit: scsi sendcmd: retryable error
CDB:  1B 00 00 00 02 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
cdrecord: Cannot eject media.

(hope thats enough information for someone to help me :) )

I've tried using different CD-R and CD-RW so I know thats not the problem - a bit stuck not sure what to try

Some help would be appreciated :) 
thanks

---

### Post by smile_sunshine on 2006-11-27
have figured out it works with cdrdao if i add --driver generic-mmc-raw   :)
but not with cdrecord. But having trouble figuring out how to do anything with cdrdao - 

Is there a gui program that uses cdrdao (and not cdrecord)?
also how do I burn an iso using cdrdao??

thanks :)

---

### Post by smile_sunshine on 2006-12-02
figured this out :)   in case anyone else has the same problem: 

to burn iso using cdrdao:

make toc file 

> 
CD_ROM
TRACK MODE1
DATAFILE "myiso.iso"
ZERO 00:02:00 // post-gap

(put in correct name of iso, save -  eg as  burniso.toc)
put in same folder as iso

then   > sudo cdrdao write --device 0,0,0 --driver generic-mmc-raw -v 99  --speed 2 burniso.toc


anyone know of a gui I can use to do this tho?? 
thanks

---

