---
title: "CD burning problems"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Outfoxed on 2007-06-12
So I'm trying to burn a few mp3 files onto a standard cd-r disk, but I'm having some trouble. I put my disk in my drive(which has been successful burning with both the cd-r disk and the desired files) and tell the CD burning program to burn(I've tried both Serpentine and K3b). It starts the burn with no problems and burns the first track fine. But once the second track comes up to be burned(it doesn't seem to matter what order they are in, the problem always happens just after the start of the second) the disk is suddenly finished and ejected. Serpentine tells me that the burn was successful, but k3b gives me an error.

---

### Post by ajmorris on 2007-06-12
> **Outfoxed said:**
> So I'm trying to burn a few mp3 files onto a standard cd-r disk, but I'm having some trouble. I put my disk in my drive(which has been successful burning with both the cd-r disk and the desired files) and tell the CD burning program to burn(I've tried both Serpentine and K3b). It starts the burn with no problems and burns the first track fine. But once the second track comes up to be burned(it doesn't seem to matter what order they are in, the problem always happens just after the start of the second) the disk is suddenly finished and ejected. Serpentine tells me that the burn was successful, but k3b gives me an error.

could you please start K3B from a terminal.

go to start menu >> Accessories >> Terminal and type in the terminal k3b, after trying to burn the cd can you please post the **whole** output of the terminal.

---

### Post by Outfoxed on 2007-06-12
> **ajmorris said:**
> could you please start K3B from a terminal.

go to start menu >> Accessories >> Terminal and type in the terminal k3b, after trying to burn the cd can you please post the **whole** output of the terminal.

All i'm getting from the terminal is this:



```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```


And here's the k3b debug output if that helps any:

```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-386
Devices
-----------------------
MATSHITA UJ-840D 1.02 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-28-386
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
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-840D         '
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   35 MB (03:33.06) no preemp swab copy
Track 02: audio   34 MB (03:27.13) no preemp swab copy
Track 03: audio   33 MB (03:20.21) no preemp swab copy
Track 04: audio   30 MB (03:01.42) no preemp swab copy
Track 05: audio   37 MB (03:41.57) no preemp swab copy
Track 06: audio   42 MB (04:10.36) no preemp swab copy
Track 07: audio   36 MB (03:34.62) no preemp swab copy
Track 08: audio   33 MB (03:18.50) no preemp swab copy
Track 09: audio   33 MB (03:21.04) no preemp swab copy
Track 10: audio   34 MB (03:26.32) no preemp swab copy
Track 11: audio   41 MB (04:05.32) no preemp swab copy
Track 12: audio   45 MB (04:29.25) no preemp swab copy
Track 13: audio   34 MB (03:26.32) no preemp swab copy
Track 14: audio   38 MB (03:50.20) no preemp swab copy
Track 15: audio   29 MB (02:57.20) no preemp swab copy
Track 16: audio   39 MB (03:52.98) no preemp swab copy
Track 17: audio   21 MB (02:10.14) no preemp swab copy
Track 18: audio   19 MB (01:57.76) no preemp swab copy
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 19: audio   28 MB (02:48.65) no preemp swab copy
Total size:      657 MB (65:08.10) = 293108 sectors
Lout start:      657 MB (65:10/08) = 293108 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 66737
Starting to write CD/DVD at speed 16 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   35 MB written.
Track 01:    1 of   35 MB written (fifo  81%) [buf  95%]  71.7x.
Track 01:    2 of   35 MB written (fifo 100%) [buf  98%]   5.6x.
Track 01:    3 of   35 MB written (fifo 100%) [buf  98%]   8.5x.
Track 01:    4 of   35 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:    5 of   35 MB written (fifo 100%) [buf  97%]   8.5x.
Track 01:    6 of   35 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:    7 of   35 MB written (fifo 100%) [buf  99%]   8.5x.
Track 01:    8 of   35 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:    9 of   35 MB written (fifo 100%) [buf  98%]   8.5x.
Track 01:   10 of   35 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:   11 of   35 MB written (fifo 100%) [buf  97%]   8.4x.
Track 01:   12 of   35 MB written (fifo  98%) [buf  99%]   8.3x.
Track 01:   13 of   35 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   14 of   35 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:   15 of   35 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   16 of   35 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:   17 of   35 MB written (fifo 100%) [buf  97%]   8.4x.
Track 01:   18 of   35 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   19 of   35 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   20 of   35 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   21 of   35 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   22 of   35 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   23 of   35 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   24 of   35 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   25 of   35 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   26 of   35 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   27 of   35 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   28 of   35 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   29 of   35 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   30 of   35 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   31 of   35 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   32 of   35 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   33 of   35 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   34 of   35 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   35 of   35 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01: Total bytes read/written: 37584960/37584960 (15980 sectors).
Starting new track at sector: 16132
Track 02:    0 of   34 MB written.
Track 02:    1 of   34 MB written (fifo  85%) [buf  95%]  64.3x.
Track 02:    2 of   34 MB written (fifo 100%) [buf  98%]   5.4x.
Track 02:    3 of   34 MB written (fifo 100%) [buf  98%]   8.5x.
Track 02:    4 of   34 MB written (fifo 100%) [buf  97%]   8.1x.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 47 59 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 00 44 D9 0A 00 2B 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 17625 (valid) 
resid: 63504
cmd finished after 4.971s timeout 40s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 5016816 bytes
Writing  time:   48.067s
Average write speed  93.8x.
Min drive buffer fill was 95%
Fixating...
Fixating time:   36.087s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 735 puts and 672 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 624 times full, min fill was 78%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -tao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-spencer/k3b_audio_0_01.inf /tmp/kde-spencer/k3b_audio_0_02.inf /tmp/kde-spencer/k3b_audio_0_03.inf /tmp/kde-spencer/k3b_audio_0_04.inf /tmp/kde-spencer/k3b_audio_0_05.inf /tmp/kde-spencer/k3b_audio_0_06.inf /tmp/kde-spencer/k3b_audio_0_07.inf /tmp/kde-spencer/k3b_audio_0_08.inf /tmp/kde-spencer/k3b_audio_0_09.inf /tmp/kde-spencer/k3b_audio_0_10.inf /tmp/kde-spencer/k3b_audio_0_11.inf /tmp/kde-spencer/k3b_audio_0_12.inf /tmp/kde-spencer/k3b_audio_0_13.inf /tmp/kde-spencer/k3b_audio_0_14.inf /tmp/kde-spencer/k3b_audio_0_15.inf /tmp/kde-spencer/k3b_audio_0_16.inf /tmp/kde-spencer/k3b_audio_0_17.inf /tmp/kde-spencer/k3b_audio_0_18.inf /tmp/kde-spencer/k3b_audio_0_19.inf 


```

---

### Post by Outfoxed on 2007-06-16
Bump, I'm somehow got a full CD to burn successfully(I didn't adjust anything) but when i tried a second one I had this problem again. Help!

---

### Post by ramjet_1953 on 2007-06-16
Sometimes there are issues with permissions, with burning.

To make sure that you eliminate that just do the following:

1: In a terminal type in the following command:

[COLOR="Red"]wodim --devices[/COLOR]

This will give you a list of your CD and DVD drives and their mount locations.

2. In a termiinal type in the folling command for each of your CD/DVD drives:

[COLOR="Red"]sudo chmod o+r+rw /dev/xxx[/COLOR]    (where xxx is the mount point of your drive)

3. When finished, re-boot, just to be sure.

What this does, is to give you ownership of your CD/DVD drives.

I hope that it helps.

Regards,
Roger :cool:

---

