---
title: "Unable to burn cd's"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by bnoll on 2007-06-17
I am running ubuntu 6.10 (up to date on all updates as of 6/17/06 - running kernel version 2.6.17-11-generic) and am unable to burn data to a CD-RW with the built in nautilus burner or with gnomebaker.  Here's the output from the gnomebaker window.

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-11-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CDRW/DVD TSL462D'
Revision       : 'DE01'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Profile: 0x0010 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1362944 = 1331 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 0.006s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:    9.293s
Average write speed  16.6x.
Fixating...
Fixating time:    0.002s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.


I'd rather not upgrade to 7.04 right now, so if anyone could propose something other than that, I'd appreciate it.

Thanks in advance...

---

### Post by bnoll on 2007-06-17
Tried it in kb3 as well (I should mention that in both gnomebaker and k3b, I tried running as gksudo and it didn't work), and got the following:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
TSSTcorp CDRW/DVD TSL462D DE01 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 6241

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/X11R6/bin/cdrecord: Warning: Running on Linux-2.6.17-11-generic
/usr/X11R6/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/X11R6/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
/usr/X11R6/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CDRW/DVD TSL462D'
Revision       : 'DE01'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Profile: 0x0010 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1362944 = 1331 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data    12 MB        
Total size:       14 MB (01:23.24) = 6243 sectors
Lout start:       14 MB (01:25/18) = 6243 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 5C D8 36
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 353606
Starting to write CD/DVD at speed 4 in real TAO mode for multi session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   12 MB written.
/usr/X11R6/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 0.005s timeout 40s
/usr/X11R6/bin/cdrecord: A write error occured.
/usr/X11R6/bin/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:    9.537s
Average write speed  16.6x.
Fixating...
Fixating time:    0.002s
/usr/X11R6/bin/cdrecord: fifo had 64 puts and 1 gets.
/usr/X11R6/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/X11R6/bin/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -tao driveropts=burnfree -eject -multi -xa -tsize=6241s - 

mkisofs
-----------------------
6241
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  8.19% done, estimate finish Sun Jun 17 21:42:35 2007
 16.14% done, estimate finish Sun Jun 17 21:42:04 2007
 24.08% done, estimate finish Sun Jun 17 21:41:54 2007

mkisofs command:
-----------------------
/usr/X11R6/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3bhAvqma.tmp -rational-rock -hide-list /tmp/kde-root/k3b3ClSic.tmp -joliet -hide-joliet-list /tmp/kde-root/k3bgsufOa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3bKtLhab.tmp

---

### Post by bnoll on 2007-06-18
I should also add that the CD-RW I tried working with works just fine when I erase and burn to it in Windows XP... so the cd can be ruled out as a problem.

Any thoughts at all would be greatly appreciated.  I've googled around, and found a bunch of other folks having burning issues, but mostly in 7.0.4... and found nothing specific enough in terms of solution to run with it.

---

### Post by bnoll on 2007-06-18
A little more information hoping it will be useful to someone to help me narrow this problem down and resolve it.

I tried Brasero as well, still can't burn to the CD-RW.

If anyone has any ideas, I'd really appreciate it.  Or, if this would be better located in a different forum, please just let me know.

TIA...

Bryan

---

### Post by bnoll on 2007-06-18
Obvious bump.  Anyone that could throw me any kind of bone at all, it would be greatly appreciated.

---

### Post by K-Starz on 2007-06-19
Hey, I know the answer!! :)

I've struggled with this ever since kernel 2.6. Apparently the guy who makes cdrecord hates all of us and didn't want to make his program actually work.
So someone has a workaround, called cdrskin. It's like an emulation layer that makes stupid cdrecord work.

Follow the directions on this page :

[https://help.ubuntu.com/community/K3BHowto](https://help.ubuntu.com/community/K3BHowto)

which is based on this, maybe more complete:

[http://scdbackup.sourceforge.net/k3b_on_cdrskin.html](http://scdbackup.sourceforge.net/k3b_on_cdrskin.html)

I installed cdrskin with apt-get. Added the path to k3b and scanned, then set cdrskin as the default.

Works beautifully! Finally!

---

### Post by K-Starz on 2007-06-19
It seems I don't even have libburn2 installed. Maybe I should.

---

### Post by st33med on 2007-06-19
Thank you for that link. I have had a problem with burning on K3B, and, from what it said, it might be because my hard drive is a SATA.

Currently I am away from my computer, so I put a post on this to keep track of it.

---

### Post by Pygi on 2007-06-24
Hey,

cdrskin doesn't touch cdrecord at all :) All it does is emulate cdrecord command line arguments to provide a compatibility layer for applications which are used on cdrecord. It is based on libburn. Packages you are using are seriously outdated, but since you aren't using gutsy (the only one which has newer packages), and this one seems to work for you, all is fine. Please do not that the cdrskin/libburn 0.2.2 had lot of problems, and that dvd recording wasn't supported.

KR,
M.

---

### Post by bnoll on 2007-06-27
K-Starz....


Thanks a ton.  I just now got back to being able to dork with this... and those links you gave me worked like a charm.  I really appreciate it.

---

