---
title: "Problem Burning Audio CD"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by vegipowrd on 2007-12-09
I'm getting a strange problem when burning audio CDs.  To be fair, I haven't tried burning data discs yet.  I'm running 7.10 on a Dell Inspiron 1000.  

I plop the disc in and Serpentine is smart enough to recognize things and get moving.  I load up a play list and start to burn.  The progress bar moves about half way (this takes several minutes) and then I get a message: "Error while writing to disc.  Try a lower speed."  But, eh hum, I'm at the lowest speed Serpentine allows (x4).  

When I do this in Rhythmbox it converts the files and then stalls out at the beginning of the "Preparing disc" portion.  Rhythmbox produces the same message. 

Reading another thread, I tried starting serpentine using terminal as ```
serpentine -d
```  The output that looked the most relevant is what I listed at the bottom. 

Thanks for any help you can give here.

> 
wodim stderr: Linux sg driver version: 3.5.27
wodim stderr: Wodim version: 1.1.6
wodim stderr: SCSI buffer size: 64512
wodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
wodim stdout: TOC Type: 0 = CD-DA
wodim stderr: communication breaks or freezes immediately after that.
wodim stdout: Driveropts: 'burnfree'
wodim stdout: Device type    : Removable CD-ROM
wodim stdout: Version        : 5
wodim stdout: Response Format: 2
wodim stdout: Capabilities   : 
wodim stdout: Vendor_info    : 'QSI     '
wodim stdout: Identification : 'CDRW/DVD SBW242C'
wodim stdout: Revision       : 'UQ81'
wodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
wodim stdout: Current: 0x0009 (CD-R)
wodim stdout: Profile: 0x0010 (DVD-ROM) 
wodim stdout: Profile: 0x0008 (CD-ROM) 
wodim stdout: Profile: 0x0009 (CD-R) (current)
wodim stdout: Profile: 0x000A (CD-RW) 
wodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
wodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
wodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim stdout: Drive buf size : 1959936 = 1914 KB
wodim stdout: FIFO size      : 16777216 = 16384 KB
wodim stderr: Speed set to 4226 KB/s
wodim stdout: Track 01: audio   43 MB (04:20.44) no preemp pad copy
wodim stdout: Track 02: audio   34 MB (03:23.36) no preemp pad copy
wodim stdout: Track 03: audio   35 MB (03:29.13) no preemp pad copy
wodim stdout: Track 04: audio   48 MB (04:49.59) no preemp pad copy
wodim stdout: Track 05: audio   52 MB (05:09.39) no preemp pad copy
wodim stdout: Track 06: audio   26 MB (02:37.36) no preemp pad copy
wodim stdout: Track 07: audio   40 MB (03:59.80) no preemp pad copy
wodim stdout: Track 08: audio   59 MB (05:55.50) no preemp pad copy
wodim stdout: Track 09: audio  105 MB (10:26.31) no preemp pad copy
wodim stdout: Total size:      448 MB (44:26.98) = 200024 sectors
wodim stdout: Lout start:      448 MB (44:28/74) = 200024 sectors
wodim stdout: Current Secsize: 2048
wodim stdout: ATIP info from disk:
wodim stdout:   Indicated writing power: 4
wodim stdout:   Is not unrestricted
wodim stdout:   Is not erasable
wodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
wodim stdout:   ATIP start of lead in:  -12508 (97:15/17)
wodim stdout:   ATIP start of lead out: 359845 (79:59/70)
wodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
wodim stdout: Manuf. index: 22
wodim stdout: Manufacturer: Ritek Co.
wodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 159821
wodim stdout: Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
wodim stdout: Last chance to quit, starting real write i   0 seconds. Operation starts.
wodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
wodim stdout: Performing OPC...
wodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
wodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
wodim stderr: status: 0x2 (CHECK CONDITION)
wodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 00 00 00
wodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
wodim stderr: Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
wodim stderr: Sense flags: Blk 0 (not valid) 
wodim stderr: cmd finished after 191.546s timeout 60s
wodim stderr: wodim: OPC failed.
wodim stderr: Errno: 5 (Input/output error), prevent/allow medium removal scsi sendcmd: fatal error
wodim stderr: CDB:  1E 00 00 00 00 00
wodim stderr: cmd finished after 0.000s timeout 40s
wodim stderr: Errno: 5 (Input/output error), start/stop unit scsi sendcmd: fatal error
wodim stderr: CDB:  1B 00 00 00 02 00
wodim stderr: cmd finished after 0.000s timeout 40s
wodim stderr: wodim: Cannot eject media.
wodim stdout: Writing  time:  191.601s
wodim stderr: wodim: fifo had 255 puts and 0 gets.
wodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
process stdout: HUP
process stderr: HUP
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/serpentine/recording.py", line 283, in __thread
    self.preferences.writeFlags)
GError: Error while writing to disc.  Try a lower speed.

---

### Post by nikoPSK on 2007-12-09
as it says, try a lower speed. Also try disabling compiz whilst you burn the cd.

---

### Post by vegipowrd on 2007-12-09
I actually didn't know compiz was on by default.  I guess I should have read that already.  

How exactly do I disable it?  Is it more than just going to Settings->Appearence and setting Visual Effects to none?  This is how mine is already set, but I get the feeling I'm not finished.

---

### Post by nikoPSK on 2007-12-09
goto:

System > Preferences > Appearance

then goto the "Visual effects" tab and set it to none.

---

### Post by vegipowrd on 2007-12-09
It's already set that way.  

Any other ideas to try?

---

### Post by nikoPSK on 2007-12-09
k3b always worked for me... even with desktop effects on. Try that. :KS

---

### Post by vegipowrd on 2007-12-09
I have heard good things about k3b, but I'd rather not touch KDE with this rather old machine.  I'm reading some of the k3b docs right now to see if things will work.  

Prepare yourself for some serious noob questions.  I understand that some KDE programs can run in Gnome, but with a performance hit.  Is this true?  I still get a bit conused about where the desktop system begins and ends. 

Other than that, I'm not totally convinced that the problems I'm having are only preformance issues.

---

### Post by nikoPSK on 2007-12-09
I don't like KDE either (in ubuntu, in other distros, it's fine;)), but this is a marvel of an app and is the only KDE app I will put on ubuntu. I suggest you try it.

---

### Post by vegipowrd on 2007-12-10
I got k3b fired up.  It does look great, but I'm still having the same problems.  One great feature of k3b is how it gives the debugger output at the end if you want it.  

The debugger says the following.  

> System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
QSI CDRW/DVD SBW242C UQ81 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 1134
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'CDRW/DVD SBW242C'
Revision       : 'UQ81'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1959936 = 1914 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   35 MB (03:33.53) no preemp swab copy
Track 02: audio   43 MB (04:21.30) no preemp swab copy
Track 03: audio   26 MB (02:36.29) no preemp swab copy
Track 04: audio   41 MB (04:09.16) no preemp swab copy
Track 05: audio   40 MB (03:59.62) no preemp swab copy
Track 06: audio   16 MB (01:40.62) no preemp swab copy
Track 07: audio   59 MB (05:52.00) no preemp swab copy
Track 08: audio   44 MB (04:25.52) no preemp swab copy
Track 09: audio   16 MB (01:36.24) no preemp swab copy
Track 10: audio   32 MB (03:14.38) no preemp swab copy
Total size:      358 MB (35:28.69) = 159652 sectors
Lout start:      358 MB (35:30/52) = 159652 sectors
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
Speed set to 3522 KB/s
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 200193
Starting to write CD/DVD at speed  20.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/wodim: faio_wait_on_buffer for writer timed out.
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 00 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 331.548s timeout 200s
/usr/bin/wodim: OPC failed.
Errno: 5 (Input/output error), prevent/allow medium removal scsi sendcmd: fatal error
CDB:  1E 00 00 00 00 00
cmd finished after 0.000s timeout 200s
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: fatal error
CDB:  1B 00 00 00 02 00
cmd finished after 0.001s timeout 200s
/usr/bin/wodim: Cannot eject media.
Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 200193
Errno: 5 (Input/output error), prevent/allow medium removal scsi sendcmd: fatal error
CDB:  1E 00 00 00 00 00
cmd finished after 0.002s timeout 200s
Writing  time:  331.580s
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: fatal error
CDB:  1B 00 00 00 02 00
cmd finished after 0.002s timeout 200s
/usr/bin/wodim: Cannot eject media.
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=20 -dao driveropts=burnfree textfile=/tmp/k3bDg5rYb.dat -eject -useinfo -audio /tmp/kde-amy/k3b_audio_0_01.inf /tmp/kde-amy/k3b_audio_0_02.inf /tmp/kde-amy/k3b_audio_0_03.inf /tmp/kde-amy/k3b_audio_0_04.inf /tmp/kde-amy/k3b_audio_0_05.inf /tmp/kde-amy/k3b_audio_0_06.inf /tmp/kde-amy/k3b_audio_0_07.inf /tmp/kde-amy/k3b_audio_0_08.inf /tmp/kde-amy/k3b_audio_0_09.inf /tmp/kde-amy/k3b_audio_0_10.inf 



---

### Post by nikoPSK on 2007-12-10
sorry, beyond me now. Hope you resolve this.

---

### Post by gupta_sumesh63 on 2007-12-10
Try cleaning your CD-ROM lens using a cleaning disk or some solution.
Secondly certain medias (CDs) are considered as worthless by Ubuntu and data cannot be written on it. It is a suggestion to change the blank CD and use another(of some other make and slightly costly).
I am sure that'll solve your problem.you may  try the following code to write.

> cdrecord dev=/dev/scd0 speed=0 driveropts=burnfree -v -audio path/to/your/music_files.

here /dev/scd0 is your CD-ROM device name
path/to/your/music_files is the absolute path to your music files.
If your files are in /home/yourname/mymusic, then path/to...... will be /home/yourname/mymusic/*.mp3.
Hope this helps

---

### Post by rockinlinux on 2007-12-10
you should use a high quality cd, cheap one seem to seldom work.

---

