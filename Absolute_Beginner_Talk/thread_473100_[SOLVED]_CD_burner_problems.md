---
title: "[SOLVED] CD burner problems"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-06-13
I've installed AptOnCD to archive my updates for when I install Ubuntu on my computer at home.  However, I can't get the disc image file to burn to the disc.  I've tried old and new CD-RWs, CD-Rs without success.  I get an "Error Writing Disc" message.  When I try a brand-new disc, I get the same error followed by "Try writing at a slower speed", even when I select 1x as my write speed.   What must I do to get my CD drive to write to disc?

---

### Post by jhenager on 2007-06-13
Check if it is the burning software. Use Synaptic or Add/Remove to install K3b. If that also gives you an error, then I would check the drive.

---

### Post by lee292 on 2007-06-13
Have K3b installed, but no discs with me.  Will try it tomorrow.  However, the CD burner works OK with Window$.

---

### Post by ramjet_1953 on 2007-06-14
You may have a permissions issue here:

Firstly, type this into a terminal:

[COLOR="Red"]wodim --devices[/COLOR]

This will give you a list of your CD and DVD drives.

Now, in a terminal again, give yourseif full access to those drives:

[COLOR="Red"]sudo chmod o+r+rw /dev/xxx [/COLOR] (where xxx is the device listed in the [COLOR="Blue"]wodim[/COLOR] command)

Do this for each device.

Then re-start.

Hopefully, this will allow you to burn.

Regards,
Roger :cool:

---

### Post by lee292 on 2007-09-09
Tried this in terminal but it doesn't recognize the command "wodim".  Anyway, I tried k3b again and the log came out as follows: 

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-12-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4240N E112 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 11505

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-12-generic
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
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4240N'
Revision       : 'E112'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1705200 = 1665 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data    22 MB        
Total size:       25 MB (02:33.42) = 11507 sectors
Lout start:       26 MB (02:35/32) = 11507 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 2
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -12900 (97:10/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 48
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Manufacturer is unknown because of the orange forum embargo.
As the orange forum likes to get money for recent information,
it may be that this media does not use illegal manufacturer coding.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 348342
Starting to write CD/DVD at speed 4 in real TAO mode for multi session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
/usr/bin/X11/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 7.857s timeout 60s
/usr/bin/X11/cdrecord: OPC failed.
Writing  time:   10.773s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -tao driveropts=burnfree -eject -multi -xa -tsize=11505s - 

mkisofs
-----------------------
11505
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  4.44% done, estimate finish Mon Sep  3 11:54:09 2007
  8.75% done, estimate finish Mon Sep  3 11:53:36 2007
 13.06% done, estimate finish Mon Sep  3 11:53:24 2007
 17.51% done, estimate finish Mon Sep  3 11:53:19 2007

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-morris/k3bklMU0b.tmp -rational-rock -hide-list /tmp/kde-morris/k3b8cGZBb.tmp -joliet -hide-joliet-list /tmp/kde-morris/k3b1aIj8b.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-morris/k3bYY5yAb.tmp 

```
 

It looks like cdrecord doesn't like my kernel.  I'm still using Edgy but I keep it updated.  Would deleting the cd recording part of the system and starting over help, and if so, what components do I need to delete and what other parts do I need to install to get my CD burner going again?

---

### Post by n3tfury on 2007-09-09
> Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 7.857s timeout 60s
/usr/bin/X11/cdrecord: OPC failed.

Power calibration errors are sometimes because of bad media or the drive is going belly up.  :/

---

### Post by lee292 on 2008-02-15
> **n3tfury said:**
> Power calibration errors are sometimes because of bad media or the drive is going belly up.  :/

That's what it was.  Replaced the drive and now I can burn CDs! Thanks!

---

