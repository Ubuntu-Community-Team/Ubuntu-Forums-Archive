---
title: "Can't burn audio cds"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-05-29
I can burn data cds but not audio. Serpentine goes off saying it is preparing files, but nothing happens, and you cannot even kill the dialog box. 

Someone elsewhere suggested gnomebaker, so I installed it, and when it gets underway it fails with the following message: 

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-RW 52X24     '
Revision       : 'K.PC'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1961344 = 1915 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
pregap1: -1
Track 01: audio   14 MB (01:25.00) no preemp pad     
Track 02: audio   29 MB (02:54.07) no preemp pad     
Track 03: audio   11 MB (01:05.61) no preemp pad     
Track 04: audio   11 MB (01:09.33) no preemp pad     
Track 05: audio   62 MB (06:09.85) no preemp pad     
Track 06: audio   20 MB (02:03.25) no preemp pad     
Track 07: audio   50 MB (05:00.52) no preemp pad     
Track 08: audio   12 MB (01:13.09) no preemp pad     
Track 09: audio   38 MB (03:49.07) no preemp pad     
Track 10: audio   18 MB (01:50.92) no preemp pad     
Track 11: audio   36 MB (03:34.79) no preemp pad     
Track 12: audio   15 MB (01:31.14) no preemp pad     
Track 13: audio   30 MB (03:02.12) no preemp pad     
Track 14: audio   39 MB (03:55.26) no preemp pad     
Total size:      395 MB (39:10.20) = 176265 sectors
Lout start:      395 MB (39:12/15) = 176265 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11849 (97:24/01)
  ATIP start of lead out: 359847 (79:59/72)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 25
Manufacturer: Taiyo Yuden Company Limited
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 183582
Forcespeed is OFF.
Starting to write CD/DVD at speed 4 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 25.594s timeout 60s
cdrecord: OPC failed.
Writing  time:   28.651s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
=========================================

What does all this mean?

Gary

---

### Post by nalmeth on 2006-05-29
The only thing I could pick out that made any sense to me was the permission error's at the start. I don't use gnomebaker, so I don't know how to configure it.
Sorry to recommend yet ANOTHER program for one task, but rather than running gnomebaker with sudo, try K3B (sudo apt-get install k3b). If you run into these permission problems again, you can go into Settings --> K3B Settings and fix things there.

Serpentine (when I used it) seemed to require the files to be wav beforehand, so I used soundconverter to convert all my files to wav before burning.

Hopefully that helps some.

---

