---
title: "Unable to burn cd"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by BjarneJ on 2007-02-11
I have tried Gnomebaker, K3b, Brasero without any luck. This is from K3B (as root):

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
LG DVD-ROM DRD8120B 1.03 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

LG CD-RW CED-8080B 1.06 (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]
Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/X11R6/bin/cdrecord: Warning: Running on Linux-2.6.17-11-generic
/usr/X11R6/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/X11R6/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/X11R6/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Text len: 1188
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
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
Vendor_info    : 'LG      '
Identifikation : 'CD-RW CED-8080B '
Revision       : '1.06'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
Drive DMA Speed: 126494 kB/s 718x CD 91x DVD
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   46 MB (04:38.92) no preemp swab copy
Track 02: audio   35 MB (03:32.98) no preemp swab copy
Track 03: audio   31 MB (03:04.30) no preemp swab copy
Track 04: audio   31 MB (03:08.81) no preemp swab copy
Track 05: audio   52 MB (05:12.93) no preemp swab copy
Track 06: audio   45 MB (04:28.28) no preemp swab copy
Track 07: audio   38 MB (03:46.33) no preemp swab copy
Track 08: audio   28 MB (02:51.42) no preemp swab copy
Track 09: audio   47 MB (04:40.58) no preemp swab copy
Track 10: audio   51 MB (05:06.92) no preemp swab copy
Track 11: audio   24 MB (02:25.80) no preemp swab copy
Track 12: audio   36 MB (03:37.66) no preemp swab copy
Track 13: audio   36 MB (03:36.58) no preemp swab copy
Track 14: audio   33 MB (03:18.69) no preemp swab copy
Track 15: audio   36 MB (03:37.05) no preemp swab copy
Track 16: audio   36 MB (03:36.40) no preemp swab copy
Track 17: audio   30 MB (03:01.09) no preemp swab copy
Track 18: audio   40 MB (04:01.20) no preemp swab copy
Track 19: audio   43 MB (04:21.30) no preemp swab copy
Track 20: audio   34 MB (03:23.81) no preemp swab copy
Track 21: audio   23 MB (02:21.20) no preemp swab copy
Total size:      786 MB (77:52.32) = 350424 sectors
Lout start:      786 MB (77:54/24) = 350424 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 9425
Starting to write CD/DVD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/X11R6/bin/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF CF AF 00 02 94 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63360
cmd finished after 200.213s timeout 200s
/usr/X11R6/bin/cdrecord: Could not write Lead-in.
/usr/X11R6/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/X11R6/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
SAO startsec: -12369
Writing lead-in...
write CD-Text data: error after 0 bytes
Writing  time:  204.547s

cdrecord command:
-----------------------
/usr/X11R6/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=8 -dao textfile=/tmp/kde-root/k3bcw2AGb.dat -eject -useinfo -audio -shorttrack /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf /tmp/kde-root/k3b_audio_0_05.inf /tmp/kde-root/k3b_audio_0_06.inf /tmp/kde-root/k3b_audio_0_07.inf /tmp/kde-root/k3b_audio_0_08.inf /tmp/kde-root/k3b_audio_0_09.inf /tmp/kde-root/k3b_audio_0_10.inf /tmp/kde-root/k3b_audio_0_11.inf /tmp/kde-root/k3b_audio_0_12.inf /tmp/kde-root/k3b_audio_0_13.inf /tmp/kde-root/k3b_audio_0_14.inf /tmp/kde-root/k3b_audio_0_15.inf /tmp/kde-root/k3b_audio_0_16.inf /tmp/kde-root/k3b_audio_0_17.inf /tmp/kde-root/k3b_audio_0_18.inf /tmp/kde-root/k3b_audio_0_19.inf /tmp/kde-root/k3b_audio_0_20.inf /tmp/kde-root/k3b_audio_0_21.inf 

I don't have any problems with the drive when using windows. Any ideas on this?

---

### Post by tbroderick on 2007-02-11
Have you tried any other modes besides SAO like TAO?

---

### Post by BjarneJ on 2007-02-12
[SIZE="2"]No, reason being that I don't know how I specify that I want to burn with TAO rather than SAO .[/SIZE]

---

### Post by BjarneJ on 2007-02-13
[SIZE="2"]Ok, found out how to burn with TAO, still unable to burn though.[/SIZE]

---

### Post by DealerMan on 2007-03-30
I've had trouble since kernel 2.6 with FC6 and now Ubuntu 6.10 Edgy trying to burn or even read CD's (but only very minor problems with DVD's).  I have trouble reading CD-R/RW when I just insert them into my Plextor PX708A drive without bringing up K3B.

BjarneJ, I get the same error message you have in your post about kernel issues.

---

### Post by trent dillman on 2007-03-30
...

---

