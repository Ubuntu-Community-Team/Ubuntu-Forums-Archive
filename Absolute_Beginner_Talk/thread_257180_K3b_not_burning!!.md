---
title: "K3b not burning!!"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-14
I drag and drop the files in K3b, then press burn and when it starts, after 30 seconds it stops and says it was unsuccessful.
Here is the debugging output (I have no idea whatsoever what it means):

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
MATSHITA UJDA340 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; SAO/R96P; SAO/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
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
Vendor_info    : 'MATSHITA'
Identifikation : 'UJDA340         '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
Drive buf size : 1359872 = 1328 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
pregap1: -1
Track 01: audio   80 MB (07:56.60) no preemp swab copy
Track 02: audio   21 MB (02:05.20) no preemp swab copy
Track 03: audio   26 MB (02:39.80) no preemp swab copy
Track 04: audio   26 MB (02:40.00) no preemp swab copy
Track 05: audio   82 MB (08:12.20) no preemp swab copy
Track 06: audio  160 MB (15:53.20) no preemp swab copy
Track 07: audio   27 MB (02:42.70) no preemp swab copy
Track 08: audio   37 MB (03:40.30) no preemp swab copy
Total size:      462 MB (45:50.01) = 206251 sectors
Lout start:      462 MB (45:52/01) = 206251 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11746 (97:25/29)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 8
Manufacturer: Hitachi Maxell, Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 153598
Starting to write CD/DVD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 3.763s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 0 K BSize: 1525 K
Starting new track at sector: 0
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0C 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.002s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
Track 01:    0 of   80 MB written.
write track data: error after 0 bytes
Writing  time:   15.905s
Average write speed 313.2x.
Fixating...
Fixating time:    0.006s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=8 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-justin/k3b_audio_0_01.inf /tmp/kde-justin/k3b_audio_0_02.inf /tmp/kde-justin/k3b_audio_0_03.inf /tmp/kde-justin/k3b_audio_0_04.inf /tmp/kde-justin/k3b_audio_0_05.inf /tmp/kde-justin/k3b_audio_0_06.inf /tmp/kde-justin/k3b_audio_0_07.inf /tmp/kde-justin/k3b_audio_0_08.inf 



So what do I do?
Thanks!
Justin

---

### Post by Sef on 2006-09-14
What are your computer specs?  Are you running Kubuntu, Gnome, or other?

---

### Post by woodlandjustin on 2006-09-14
> **Sef said:**
> What are your computer specs?  Are you running Kubuntu, Gnome, or other?

The latest version of Ubuntu, Dapper, and Gnome. On a laptop. Windows burned CDs fine.

---

### Post by woodlandjustin on 2006-09-14
> **Sef said:**
> What are your computer specs?  Are you running Kubuntu, Gnome, or other?

Maybe I didn't give you enough computer specs? Hmm, it is a Toshiba Satellite  31CDT laptop. If you need more specs perhaps you can instruct me how to get them for you?
Justin

---

