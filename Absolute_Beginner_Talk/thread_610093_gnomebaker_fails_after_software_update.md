---
title: "gnomebaker fails after software update"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ChrisC on 2007-11-11
Howdy folks -

I'm running Dapper / 6.06 LTS -- looking forward to the next LTS in the spring.  This morning I did a regular software update ( security / crash updates only ).  Now GnomeBaker won't burn an audio CD for me.

The output implies that it's not working in TAO mode.  But I didn't change anything, just did the security update, and it had worked before.  I'm assuming that the tao mode error could be a red herring, and the problem is actually something else.

Any ideas?

Here is the output:

```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-29-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PLEXTOR '
Identifikation : 'DVDR   PX-712A  '
Revision       : '1.04'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
pregap1: -1
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.

```

---

### Post by ChrisC on 2007-11-13
help?

---

