---
title: "GnomeBaker issue..."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-09-04
My DVD/CD writer is fine, I'll state first off. I've tried it on my other computers and it works, I swear. Xubuntu recodnizes it as a CD drive, that can write, and I can read CDs off of it and stuff.

Now, I've been to the RestrictedFormat wiki, it said to install some packages for GnomeBaker to use MP3 files. Got them installed.

So now I'm trying to burn a Audio CD. This is the error window I get.

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
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
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 1250
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 04 E2 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.008s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   17.888s
Average write speed 605.6x.
Fixating...
Fixating time:    0.013s
cdrecord: Input/output error. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 480s
cmd finished after 0.005s timeout 480s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
```

CD is still blank, I suppose. And like I mentioned I'm running Xubuntu. Any ideas?

---

### Post by croak77 on 2006-09-04
Try running it with gksudo gnomebaker.

---

### Post by SZF2001 on 2006-09-04
I ran it with that, I just get the same message back...

What is the name of that burning software in the origional Ubuntu? Like, it comes with it, or something? Maybe I'll just use that.

---

### Post by nudnik on 2006-09-05
I have found that K3b is the least problematic linux burning program. I used gnomebaker and the default software when I first began using Ubuntu and experienced a number of errors. Ubuntu Dapper with the latest updates and K3b installed works very well, at least with my hardware.

---

