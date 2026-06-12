---
title: "wrong k3b?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-05-31
Hi there: i use 6.06 and when trying to burn a DVD in k3b I get:

> System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4163B A103 (/dev/hda, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

SONY DVD-ROM DDU1621 S3.5 (/dev/hdb, ) at  [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-28-386
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
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4163B'
Revision       : 'A103'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13933 kB/s 79x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
pregap1: -1
Track 01: audio   19 MB (01:53.66) no preemp swab copy
Track 02: audio   30 MB (02:58.60) no preemp swab copy
Track 03: audio   37 MB (03:41.57) no preemp swab copy
Track 04: audio   41 MB (04:07.52) no preemp swab copy
Track 05: audio   31 MB (03:05.86) no preemp swab copy
Track 06: audio   38 MB (03:49.46) no preemp swab copy
Track 07: audio   29 MB (02:52.48) no preemp swab copy
Track 08: audio   28 MB (02:51.89) no preemp swab copy
Track 09: audio   14 MB (01:27.29) no preemp swab copy
Total size:      270 MB (26:48.36) = 120627 sectors
Lout start:      270 MB (26:50/27) = 120627 sectors
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
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 239218
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   19 MB written.
Track 01:    1 of   19 MB written (fifo  76%) [buf  94%]   3.3x.
Track 01:    2 of   19 MB written (fifo  51%) [buf 100%]   4.2x.
Track 01:    3 of   19 MB written (fifo  34%) [buf  99%]   4.2x.
Track 01:    4 of   19 MB written (fifo   7%) [buf  94%]   2.3x.
Track 01:    5 of   19 MB written (fifo   7%) [buf  52%]   1.9x.
Track 01:    6 of   19 MB written (fifo   6%) [buf  44%]   3.8x.
Track 01:    7 of   19 MB written (fifo   6%) [buf  78%]   1.7x.
Track 01:    8 of   19 MB written (fifo   4%) [buf  90%]   2.4x.
Track 01:    9 of   19 MB written (fifo   4%) [buf  65%]   1.9x.
Track 01:   10 of   19 MB written (fifo   3%) [buf  51%]   3.6x.
Track 01:   11 of   19 MB written (fifo   3%) [buf  29%]   3.4x.
Track 01:   12 of   19 MB written (fifo   1%) [buf  96%]   4.0x.
Track 01:   13 of   19 MB written (fifo   1%) [buf  81%]   2.3x.
Track 01:   14 of   19 MB written (fifo   4%) [buf  65%]   1.8x.
Track 01:   15 of   19 MB written (fifo   3%) [buf  96%]   2.8x.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 1A 28 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 10 34 1D 00 80 10 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 24.786s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 15748992 bytes
Writing  time:  128.188s
Average write speed  12.6x.
Min drive buffer fill was 29%
Fixating...
Fixating time:    0.004s
/usr/bin/X11/cdrecord: fifo had 285 puts and 249 gets.
/usr/bin/X11/cdrecord: fifo was 43 times empty and 0 times full, min fill was 0%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hda speed=4 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-johnnyw/k3b_audio_0_01.inf /tmp/kde-johnnyw/k3b_audio_0_02.inf /tmp/kde-johnnyw/k3b_audio_0_03.inf /tmp/kde-johnnyw/k3b_audio_0_04.inf /tmp/kde-johnnyw/k3b_audio_0_05.inf /tmp/kde-johnnyw/k3b_audio_0_06.inf /tmp/kde-johnnyw/k3b_audio_0_07.inf /tmp/kde-johnnyw/k3b_audio_0_08.inf /tmp/kde-johnnyw/k3b_audio_0_09.inf 



---

### Post by doobit on 2007-05-31
Use Synaptic to install the latest version of cdrecord. K3B uses cdrecord and looks like your version may be old or corrupted.

---

### Post by johnnyw on 2007-05-31
tried and got this:

> System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4163B A103 (/dev/hda, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

SONY DVD-ROM DDU1621 S3.5 (/dev/hdb, ) at  [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
K3b
-----------------------
Size of filesystem calculated: 375895

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-28-386
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
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Identifikation : 'DVDRAM GSA-4163B'
Revision       : 'A103'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 2293 kB/s 13x CD 1x DVD
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: WARNING: Data may not fit on current disk.
/usr/bin/X11/cdrecord: Notice: Overburning active. Trying to write more than the official disk capacity.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   734 MB        
Total size:      843 MB (83:31.93) = 375895 sectors
Lout start:      843 MB (83:33/70) = 375895 sectors
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
Blocks total: 359845 Blocks current: 359845 Blocks remaining: -16050
Starting to write CD/DVD at speed 40 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
/usr/bin/X11/cdrecord: DMA speed too slow (OK for 11x). Cannot write at speed 40x.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  734 MB written.
Track 01:    1 of  734 MB written (fifo  76%) [buf  74%]  15.4x.
Track 01:    2 of  734 MB written (fifo  68%) [buf  68%]  15.7x.
Track 01:    3 of  734 MB written (fifo  98%) [buf  21%]  10.9x.
Track 01:    4 of  734 MB written (fifo  96%) [buf  91%]   5.8x.
Track 01:    5 of  734 MB written (fifo  75%) [buf  86%]  16.2x.
Track 01:    6 of  734 MB written (fifo  90%) [buf  39%]  12.1x.
Track 01:    7 of  734 MB written (fifo  68%) [buf  33%]  15.4x.
Track 01:    8 of  734 MB written (fifo  53%) [buf  16%]  14.2x.
Track 01:    9 of  734 MB written (fifo  28%) [buf  10%]  16.1x.
Track 01:   10 of  734 MB written (fifo   6%) [buf  62%]  15.6x.
Track 01:   11 of  734 MB written (fifo  98%) [buf  28%]   4.2x.
Track 01:   12 of  734 MB written (fifo  92%) [buf  90%]   5.7x.
Track 01:   13 of  734 MB written (fifo  73%) [buf  84%]  16.1x.
Track 01:   14 of  734 MB written (fifo  48%) [buf  72%]  15.6x.
Track 01:   15 of  734 MB written (fifo  35%) [buf  67%]  15.1x.
Track 01:   16 of  734 MB written (fifo  20%) [buf  54%]  14.7x.
Track 01:   17 of  734 MB written (fifo   1%) [buf  50%]  16.0x.
Track 01:   18 of  734 MB written (fifo   7%) [buf  21%]  13.1x.
Track 01:   19 of  734 MB written (fifo  14%) [buf  55%]  13.5x.
Track 01:   20 of  734 MB written (fifo 100%) [buf  34%]   5.1x.
Track 01:   21 of  734 MB written (fifo  85%) [buf  29%]  15.2x.
Track 01:   22 of  734 MB written (fifo  59%) [buf  24%]  15.5x.
Track 01:   23 of  734 MB written (fifo  37%) [buf  18%]  16.0x.
Track 01:   24 of  734 MB written (fifo  10%) [buf  13%]  15.4x.
Track 01:   25 of  734 MB written (fifo  23%) [buf  69%]  11.4x.
Track 01:   26 of  734 MB written (fifo  98%) [buf  42%]   4.5x.
Track 01:   27 of  734 MB written (fifo  98%) [buf  14%]   4.5x.
Track 01:   28 of  734 MB written (fifo 100%) [buf  15%]   4.8x.
Track 01:   29 of  734 MB written (fifo  89%) [buf  20%]  14.3x.
Track 01:   30 of  734 MB written (fifo  98%) [buf   9%]   4.7x.
Track 01:   31 of  734 MB written (fifo  82%) [buf  84%]  15.0x.
Track 01:   32 of  734 MB written (fifo 100%) [buf  14%]   2.7x.
Track 01:   33 of  734 MB written (fifo  95%) [buf  39%]   5.0x.
Track 01:   34 of  734 MB written (fifo  78%) [buf  33%]  16.2x.
Track 01:   35 of  734 MB written (fifo  57%) [buf  27%]  15.6x.
Track 01:   36 of  734 MB written (fifo  46%) [buf  70%]  12.0x.
Track 01:   37 of  734 MB written (fifo  96%) [buf  41%]   4.6x.
Track 01:   38 of  734 MB written (fifo 100%) [buf  14%]   4.6x.
Track 01:   39 of  734 MB written (fifo 100%) [buf  13%]   2.9x.
Track 01:   40 of  734 MB written (fifo  92%) [buf   8%]  15.4x.
Track 01:   41 of  734 MB written (fifo 100%) [buf  33%]   4.9x.
Track 01:   42 of  734 MB written (fifo  76%) [buf  25%]  15.8x.
Track 01:   43 of  734 MB written (fifo  54%) [buf  20%]  15.6x.
Track 01:   44 of  734 MB written (fifo  29%) [buf  14%]  16.1x.
Track 01:   45 of  734 MB written (fifo 100%) [buf  26%]   4.2x.
Track 01:   46 of  734 MB written (fifo  87%) [buf  21%]  15.3x.
Track 01:   47 of  734 MB written (fifo  60%) [buf  16%]  15.6x.
Track 01:   48 of  734 MB written (fifo  35%) [buf  10%]  16.0x.
Track 01:   49 of  734 MB written (fifo   9%) [buf  62%]  15.5x.
Track 01:   50 of  734 MB written (fifo  95%) [buf  13%]   4.7x.
Track 01:   51 of  734 MB written (fifo  70%) [buf   8%]  15.5x.
Track 01:   52 of  734 MB written (fifo 100%) [buf  92%]   5.8x.
Track 01:   53 of  734 MB written (fifo  75%) [buf  86%]  15.4x.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 6B A7 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 10 34 43 00 80 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 56440832 bytes
Writing  time:   70.212s
Average write speed  71.4x.
Min drive buffer fill was 8%
Fixating...
Fixating time:    0.005s
/usr/bin/X11/cdrecord: fifo had 953 puts and 890 gets.
/usr/bin/X11/cdrecord: fifo was 5 times empty and 118 times full, min fill was 0%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hda speed=40 -dao driveropts=burnfree -eject -overburn -data -tsize=375895s - 

mkisofs
-----------------------
375895
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.14% done, estimate finish Thu May 31 18:10:28 2007
  0.27% done, estimate finish Thu May 31 17:58:35 2007
  0.40% done, estimate finish Thu May 31 17:50:22 2007
  0.54% done, estimate finish Thu May 31 17:46:08 2007
  0.67% done, estimate finish Thu May 31 18:41:03 2007
  0.80% done, estimate finish Thu May 31 18:29:57 2007
  0.93% done, estimate finish Thu May 31 18:23:46 2007
  1.07% done, estimate finish Thu May 31 18:18:57 2007
  1.20% done, estimate finish Thu May 31 18:15:21 2007
  1.33% done, estimate finish Thu May 31 18:11:14 2007
  1.46% done, estimate finish Thu May 31 18:10:07 2007
  1.60% done, estimate finish Thu May 31 18:07:01 2007
  1.73% done, estimate finish Thu May 31 18:04:29 2007
  1.86% done, estimate finish Thu May 31 18:02:18 2007
  2.00% done, estimate finish Thu May 31 18:01:15 2007
  2.13% done, estimate finish Thu May 31 18:01:03 2007
  2.26% done, estimate finish Thu May 31 18:00:11 2007
  2.40% done, estimate finish Thu May 31 17:59:26 2007
  2.53% done, estimate finish Thu May 31 17:58:45 2007
  2.66% done, estimate finish Thu May 31 17:57:28 2007
  2.80% done, estimate finish Thu May 31 17:56:20 2007
  2.93% done, estimate finish Thu May 31 17:55:19 2007
  3.06% done, estimate finish Thu May 31 17:54:23 2007
  3.20% done, estimate finish Thu May 31 17:54:02 2007
  3.33% done, estimate finish Thu May 31 17:54:13 2007
  3.46% done, estimate finish Thu May 31 17:53:26 2007
  3.59% done, estimate finish Thu May 31 17:53:11 2007
  3.73% done, estimate finish Thu May 31 17:52:28 2007
  3.86% done, estimate finish Thu May 31 17:51:49 2007
  3.99% done, estimate finish Thu May 31 17:51:39 2007
  4.12% done, estimate finish Thu May 31 17:51:04 2007
  4.26% done, estimate finish Thu May 31 17:51:18 2007
  4.39% done, estimate finish Thu May 31 17:51:32 2007
  4.52% done, estimate finish Thu May 31 17:51:00 2007
  4.66% done, estimate finish Thu May 31 17:51:14 2007
  4.79% done, estimate finish Thu May 31 17:51:26 2007
  4.92% done, estimate finish Thu May 31 17:51:17 2007
  5.06% done, estimate finish Thu May 31 17:51:10 2007
  5.19% done, estimate finish Thu May 31 17:51:02 2007
  5.32% done, estimate finish Thu May 31 17:50:36 2007
  5.46% done, estimate finish Thu May 31 17:50:29 2007
  5.59% done, estimate finish Thu May 31 17:50:24 2007
  5.72% done, estimate finish Thu May 31 17:50:18 2007
  5.86% done, estimate finish Thu May 31 17:50:46 2007
  5.99% done, estimate finish Thu May 31 17:50:40 2007
  6.12% done, estimate finish Thu May 31 17:50:34 2007
  6.25% done, estimate finish Thu May 31 17:50:29 2007
  6.39% done, estimate finish Thu May 31 17:50:23 2007
  6.52% done, estimate finish Thu May 31 17:50:03 2007
  6.65% done, estimate finish Thu May 31 17:49:44 2007
  6.78% done, estimate finish Thu May 31 17:50:09 2007
  6.92% done, estimate finish Thu May 31 17:49:50 2007
  7.05% done, estimate finish Thu May 31 17:49:31 2007
  7.18% done, estimate finish Thu May 31 17:49:14 2007
  7.32% done, estimate finish Thu May 31 17:49:11 2007
  7.45% done, estimate finish Thu May 31 17:49:07 2007
  7.58% done, estimate finish Thu May 31 17:48:51 2007
  7.72% done, estimate finish Thu May 31 17:48:49 2007
  7.85% done, estimate finish Thu May 31 17:48:46 2007

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Autocad -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-johnnyw/k3brwc4Ab.tmp -rational-rock -hide-list /tmp/kde-johnnyw/k3bAc7PUb.tmp -joliet -hide-joliet-list /tmp/kde-johnnyw/k3btgEddb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-johnnyw/k3bgmkQza.tmp 


---

