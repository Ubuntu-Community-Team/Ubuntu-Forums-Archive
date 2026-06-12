---
title: "Cannot burn CDs"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-09-16
I've tried several different CD burning programs.  I'm trying to burn an ISO image.  Even though it takes several minutes, and claims to be completed, each time my disk ends up still blank.

It's as if I have it set to simulate write only when I don't.  What's going on?

This is on a Dell Inspiron 5160.

Thanks

---

### Post by dbd on 2006-09-16
No idea why different CD burning programs would all be simulating a write. Do the CD's look blank? (CDs change colour a little when written, try half writing 300 MB of data to a CD, so that half the CD has been written on, then there should be two different colour regions on the data side of the CD). (note, colour is probably the wrong word, but there is a visible difference).

Are you sure that you have mounted the new CDs? Try ejecting the CD and putting it back in, does ubuntu recognise it is a blank CD or just open a folder with nothing it it? Or typing at the command line:
sudo mount /dev/hdc

---

### Post by Marsolin on 2006-09-16
This is just a shot in the dark, but you could try completely uninstalling cdrecord and then reinstalling it. Make sure that you use the Complete Removal option in Synaptic.

You didn't mention which burners you tried, but K3b does have a simulate checkbox on the burn page.

Are you using CD-R's or CD-RW's?  If the latter they may need to be erased first.

One other possibility is that your drive has a problem.

---

### Post by uzd4ce on 2006-09-16
I've tried X-CD-Roast, something Toaster, and Gnomebaker.  When I eject the supposedly burned cd and then put it back in the drive, I get the message about "you have inserted a blank cd" and what do you want to do with it.

The resulting CDs are definitely blank, even by looking at them.

I tried sudo mount /dev/hdc and I get the following error:
mount: can't find /dev/hdc in /etc/fstab or /etc/mtab

Thanks for any suggestions.

---

### Post by xpod on 2006-09-16
All you have to do with k3b is right click the iso and chose write to disc.
You could always try that

---

### Post by uzd4ce on 2006-09-16
So I tried K3B. It definitely is the best looking burner I've tried.  A few discs errored out partway through the burn, but finally one finished.  It's still completely blank (as are the ones that "errored" during the burn.)

The log from the burn is below.  I just noticed this line:"Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted"

Does that have something to do with the fact that it thinks its burning when it's not?

Thanks




System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4243N A102 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hda'
devname: '/dev/hda'
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
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4243N'
Revision       : 'A102'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 (current)
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1601712 = 1564 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   696 MB        
Total size:      800 MB (79:17.00) = 356775 sectors
Lout start:      800 MB (79:19/00) = 356775 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 3074
Starting to write CD/DVD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  696 MB written.
Track 01:    1 of  696 MB written (fifo 100%) [buf  99%]  10.2x.
Track 01:    2 of  696 MB written (fifo 100%) [buf  99%]  10.3x.
Track 01:    3 of  696 MB written (fifo 100%) [buf  99%]  10.6x.
<snip>
Track 01:  695 of  696 MB written (fifo 100%) [buf  99%]  10.5x.
Track 01:  696 of  696 MB written (fifo 100%) [buf  99%]  10.2x.
Track 01: Total bytes read/written: 730675200/730675200 (356775 sectors).
Writing  time:  505.908s
Average write speed   9.7x.
Min drive buffer fill was 99%
Fixating...
Fixating time:    9.865s
/usr/bin/X11/cdrecord: fifo had 11509 puts and 11509 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 11411 times full, min fill was 95%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hda speed=8 -dao driveropts=burnfree -eject -data /home/bill/Downloads/ubuntu.iso

---

### Post by bodhi.zazen on 2006-09-16
see if either of these help:

[Burn CD 1](http://ubuntuforums.org/showthread.php?t=217472)
[Burn CD 2](http://ubuntuforums.org/showthread.php?t=209547)

---

