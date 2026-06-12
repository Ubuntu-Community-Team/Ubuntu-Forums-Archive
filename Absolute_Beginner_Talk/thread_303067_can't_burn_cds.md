---
title: "can't burn cds"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by tbooher on 2006-11-19
baker and all the default cd burning (serpentine, etc) worked fine for a while. some software automatically updated, now things don't work at all. I am sure I am not the only one experencing this. Here is some diagnostic information.

kernel: 
Linux stadion 2.6.15-27-server #1 SMP Sat Sep 16 02:57:21 UTC 2006 i686 GNU/Linux

from the baker session:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
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

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX160E  '
Revision       : '1.0g'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183552 = 4085 KB
Drive DMA Speed: 2675 kB/s 15x CD 1x DVD
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.004s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:    5.081s
Average write speed 587.3x.
Fixating...
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.008s timeout 480s
cmd finished after 0.008s timeout 480s
Fixating time:    0.011s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

__________________________________________________________

any help greatly appreciated.

Tim

---

### Post by finferflu on 2006-11-19
Have you tried with Brasero? When I had issues with the default apps, Brasero usually saved my day.

Hope it helps.

---

### Post by tbooher on 2006-11-19
no -- its not a familiar app -- still, i am sure there is something simple that we can do to get the cd fixed. there are a lot of associated cd problems from other apps and I think there might be a device / permissions problem -- anyone else have any ideas?

---

### Post by tbooher on 2006-11-20
o.k. got a lead on the problem. i remember when i was trying to install matlab i was having problems getting the installer to run -- so i was unmounting and mounting the cdrom -- was it possible that the cd wasn't mounted -- also why am i emulating scsi? why do both the device and the mount point have permissions? what is a device, really anyway?

---

### Post by finferflu on 2006-11-20
Well, now that you talk about permissions, I remember that once I was not able to burn unless I started the application with sudo. For the rest I haven't got much experience, so this is how far I can help you for now...

---

