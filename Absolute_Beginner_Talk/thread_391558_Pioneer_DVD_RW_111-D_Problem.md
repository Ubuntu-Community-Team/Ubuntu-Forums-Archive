---
title: "Pioneer DVD RW 111-D Problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by tgrisier on 2007-03-23
My  Pioneer DVD RW 111-D will burn DVD's just fine but I can't get it to burn audio CD's.  I've tried GnomeBaker, Serpentine, K3B.  This has me really perplexed, especially since it will burn DVD's.

Being new to linux I'm at a loss on what to try next.

---

### Post by samp-wallah on 2007-03-23
What kind of error, if any are you getting when you try to burn an audio CD? Have you installed the MP3 libs? If you haven't it doesn't matter what burning software you use unless you are trying to burn from .ogg.

---

### Post by tgrisier on 2007-03-23
Here's what I get from K3B:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.19 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

SAMSUNG DVD-ROM SD-616E F503 (/dev/hdd, ) at /media/cdrom1 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-11-generic
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
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
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
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-111D'
Revision       : '1.19'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
pregap1: -1
Track 01: audio   50 MB (04:57.44) no preemp swab copy
Track 02: audio   43 MB (04:21.09) no preemp swab copy
Track 03: audio   50 MB (05:02.50) no preemp swab copy
Track 04: audio   49 MB (04:56.89) no preemp swab copy
Track 05: audio   46 MB (04:33.53) no preemp swab copy
Track 06: audio  165 MB (16:21.38) no preemp swab copy
Total size:      405 MB (40:12.85) = 180964 sectors
Lout start:      406 MB (40:14/64) = 180964 sectors
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
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 178881
Starting to write CD/DVD at speed 32 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
/usr/bin/X11/cdrecord: Success. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 70 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 0A 93 70 6E 0E 26 01 30 E6 08 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x01 (logical unit communication time-out) Fru 0x0
Sense flags: Blk 177434734 (not valid) 
resid: 112
cmd finished after 2.206s timeout 200s
/usr/bin/X11/cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/X11/cdrecord: Cannot send CUE sheet.
/usr/bin/X11/cdrecord: Could not write Lead-in.
Writing  time:   25.224s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=32 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-tony/k3b_audio_0_01.inf /tmp/kde-tony/k3b_audio_0_02.inf /tmp/kde-tony/k3b_audio_0_03.inf /tmp/kde-tony/k3b_audio_0_04.inf /tmp/kde-tony/k3b_audio_0_05.inf /tmp/kde-tony/k3b_audio_0_06.inf 



Unfortunately it's all greek to me.  Can you make heads or tails out of this?

---

### Post by tgrisier on 2007-03-24
Well, I have gotten my problem resolved.  The other day I installed a linksys ethernet card and that, for some reason, was interferring with my CD and DVD burning.   I removed the card a little while ago and now I can burn CD's and DVD's.  Kind of odd though.

---

### Post by 4tro on 2007-03-27
what you could try is to add an irqpoll to your bootoptions.

like this.

```
title           Ubuntu, kernel 2.6.20-13-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-13-generic root=UUID=a485ec22-d328-400e-adc6-e347dacd02b6 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.20-13-generic
boot
```

it fixed my network-card/videocard problems

---

### Post by TheMono on 2007-03-27
I'm sort of flogging this as a cureall at the moment, but:

sudo chown root:cdrom /usr/bin/cdr*
sudo chmod 4754 /usr/bin/cdr*

---

