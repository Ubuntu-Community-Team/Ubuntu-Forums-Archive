---
title: "What is a good all round CD burning program?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-10-29
I have k3b cd burning program and it often fails. I wait all that time for it to copy the cd to a temporary folder then when I put in the blank cd it often just spits it out after a minute and says it failed, and automatically erases the temporary file. I really want a cd burning program that will work! And I want to use it for everything. Burning data, copying CDs, burning WAV cds etc.
Thanks

---

### Post by Sef on 2006-10-29
Try GnomeBaker.  It is available in the repositories.  You can download it from Add/Remove.

---

### Post by 23meg on 2006-10-29
Check out graveman.

---

### Post by Marsolin on 2006-10-30
What does error message do you see when it fails?

---

### Post by woodlandjustin on 2006-10-30
> **Marsolin said:**
> What does error message do you see when it fails?

Graveman just says "operation failed". It was working last week, but I don't remember what for. Maybe I burned a data CD. Actually, can't remember what. Anyway this time I'm trying to put wav files to make an audio cd.
Don't remember the error messages for the other programs. Some of them work sometimes for some things. Very fristrating. I have gnomebaker, serpentine, k3b and graveman. At the moment noe of them are able to copy a CD! Nor put wav files to make a CD.

---

### Post by verby on 2006-10-30
If interested, check for Nero for Linux. lots of options, did not try but looks ok.

---

### Post by 3rdalbum on 2006-10-30
All CD burning programs on Linux (except maybe NeroLinux) use the same backend burning program.

Try running K3B using gksudo or kdesu:

```

gksudo k3b

```

or

```

kdesu k3b

```

---

### Post by Marsolin on 2006-10-30
You might want to try reinstalling [cdrecord]("http://linuxappfinder.com/package/cdrecord"). The has fixed problems for me in the past.

---

### Post by woodlandjustin on 2006-11-01
> **Marsolin said:**
> You might want to try reinstalling [cdrecord]("http://linuxappfinder.com/package/cdrecord"). The has fixed problems for me in the past.

Just reinstalled cdrecord. Graveman still fails. K3b fails too, and gives this output:

> System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
MATSHITA UJDA340 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; SAO/R96P; SAO/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.15-27-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
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
pregap1: -1
Track 01: audio  136 MB (13:30.29) no preemp swab copy
Track 02: audio  139 MB (13:47.49) no preemp swab copy
Track 03: audio  158 MB (15:44.22) no preemp swab copy
Track 04: audio   99 MB (09:49.80) no preemp swab copy
Total size:      533 MB (52:51.81) = 237886 sectors
Lout start:      533 MB (52:53/61) = 237886 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11746 (97:25/29)
  ATIP start of lead out: 335100 (74:30/00)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 8
Manufacturer: Hitachi Maxell, Ltd.
Blocks total: 335100 Blocks current: 335100 Blocks remaining: 97214
Starting to write CD/DVD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/usr/bin/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.631s timeout 200s
/usr/bin/cdrecord: OPC failed.
Writing  time:   10.595s
BURN-Free was never needed.
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=8 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf 







Second try with definitely untouched CDr:

> System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
MATSHITA UJDA340 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; SAO/R96P; SAO/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.15-27-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
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
pregap1: -1
Track 01: audio  136 MB (13:30.29) no preemp swab copy
Track 02: audio  139 MB (13:47.49) no preemp swab copy
Track 03: audio  158 MB (15:44.22) no preemp swab copy
Track 04: audio   99 MB (09:49.80) no preemp swab copy
Total size:      533 MB (52:51.81) = 237886 sectors
Lout start:      533 MB (52:53/61) = 237886 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11746 (97:25/29)
  ATIP start of lead out: 335100 (74:30/00)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 8
Manufacturer: Hitachi Maxell, Ltd.
Blocks total: 335100 Blocks current: 335100 Blocks remaining: 97214
Starting to write CD/DVD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
/usr/bin/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.661s timeout 200s
/usr/bin/cdrecord: OPC failed.
Writing  time:   10.605s
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=8 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf 







---

### Post by dvarsam on 2006-11-14
From what I have noticed/read,

There is _NO_ Linux OpenSource-Free application that can handle successfully what you are looking for!

...Too many bugs & crashes!!!

I am NOT even able to play VCDs on _any_ Linux OpenSource-Free program I was suggested to try-out!

Conclusion:

Your last resort should be to try "NeroLinux".
But there is a price you have to pay for it...
This is what I would like to try-out too!
I wonder whether there is a Trial version out there...

Good Luck!

P.S.> Sometimes I feel Linux is too primitive compared to Windows.
No offense to Linux fanatics - I am a Linux User too!

---

### Post by cotcot on 2006-11-14
It is audio you tried to burn. Maybe the source is protected against copy.
Maybe the cd is not suitable for your burner. Old cd-burners cannot use high speed cd. You have to feed them with low speed CD (2x).

Have your tried to burn data on a CD ?
I tried gnomebaker, graveman and it did not work. Since then I only use k3b which is working fine.

---

