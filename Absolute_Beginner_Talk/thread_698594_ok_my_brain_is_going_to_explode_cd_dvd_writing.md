---
title: "ok my brain is going to explode cd dvd writing"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by slack31337 on 2008-02-16
I have searched and read and asked on IRC and searched more all  come up with nothing substantial to help me burn music cds dvds etc.. Now i don't know if it is a bug or my hardware but i seem to remember being able to burn both cds and dvds on this hardware at some point and version of *nix whether fedora/ubuntu/slackware some random kernel... 

<rant>

The thing that annoys me most is that I am the biggest *nix evangelist I know , but stuff like this... DRIVES ME !!! And my buddies are all "well it works in windows and that is another reason why *nix is not ready for the desktop".   :( And sometimes I almost fall.. but..I forge on). To add I am trying to convert my wife over and things like this don't help

So help me fellow *nix fans and tell me for once and for all HOW  can I burn to cd or dvd and copy dvds *{Pelase don't bring politics into this as a proper os should have the capability to "shrink and burn a dvd-9}  * with out a huge clusterfark of a screwaround.... I promise If i get this figured out I will dedicate a website soley to the instructions on how to do this and post it for all to see.

Tell me what you need from me and I will post it email whatever you need to help....

</rant>

Your help is appreciated

---

### Post by PurposeOfReason on 2008-02-16
Are you using nautilus? If so, open that up and type burn:/// for the location or just pop in a blank disk and it should open for you.

For copying google devede.

---

### Post by jan quark on 2008-02-16
so for example you open up k3b
and you try to burn a cd

and what happens then, error messages? nothing? your desktop explodes?
pls some more info

thank you

---

### Post by nagius on 2008-02-16
Well I don't know any details of  your problem, please you need to be more specific. What software are u using to burn CD and DVDs. What error are you encountering.

Also I can you can tell your buddies that burning CDs is as easy in Linux as in windows, if not even easier becuase there is burning software installed in almost all versions of Linux. In windows you need to purchase such software.

---

### Post by PurposeOfReason on 2008-02-16
> **nagius said:**
> Well I don't know any details of  your problem, please you need to be more specific. What software are u using to burn CD and DVDs. What error are you encountering.

Also I can you can tell your buddies that burning CDs is as easy in Linux as in windows, if not even easier becuase there is burning software installed in almost all versions of Linux. In windows you need to purchase such software.
Just going to throw it out there that windows media player can burn and as it is a part of a standard windows install, you technically aren't paying for it.

---

### Post by slack31337 on 2008-02-16
ok so using k3b here is an ouput from the last time i tried to burn a data cd

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HP CD-Writer+ 9300 1.0b (/dev/hdc, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 990
TOC Type: 0 = CD-DA
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'HP      '
Identification : 'CD-Writer+ 9300 '
Revision       : '1.0b'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 23805 kB/s 135x CD 17x DVD
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   39 MB (03:52.21) no preemp swab copy
Track 02: audio   71 MB (07:07.62) no preemp swab copy
Track 03: audio   39 MB (03:55.05) no preemp swab copy
Track 04: audio   30 MB (03:00.14) no preemp swab copy
Track 05: audio   43 MB (04:17.52) no preemp swab copy
Track 06: audio   33 MB (03:16.68) no preemp swab copy
Track 07: audio   56 MB (05:33.09) no preemp swab copy
Track 08: audio   28 MB (02:51.60) no preemp swab copy
Track 09: audio   47 MB (04:41.21) no preemp swab copy
Track 10: audio   43 MB (04:15.74) no preemp swab copy
Track 11: audio   38 MB (03:49.30) no preemp swab copy
Track 12: audio   45 MB (04:31.54) no preemp swab copy
Track 13: audio   76 MB (07:35.16) no preemp swab copy
Track 14: audio   35 MB (03:31.05) no preemp swab copy
Total size:      628 MB (62:17.96) = 280347 sectors
Lout start:      629 MB (62:19/72) = 280347 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
Speed set to 1764 KB/s
  ATIP start of lead in:  -11080 (97:34/20)
  ATIP start of lead out: 335100 (74:30/00)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 335100 Blocks current: 335100 Blocks remaining: 54753
RBlocks total: 342460 RBlocks current: 342460 RBlocks remaining: 62113
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
SAO startsec: -11080
Writing lead-in...
Lead-in write time:   18.783s
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   39 MB written.
Track 01:    1 of   39 MB written (fifo  94%) [buf  59%] 109.2x.
Track 01:    2 of   39 MB written (fifo  87%) [buf  85%] 110.8x.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 04 89 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 FF FF D4 DE 12 00 00 00 00 0C 08 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x08 (write error - recovery failed) Fru 0x0
Sense flags: Blk -11042 (valid) 
resid: 63504
cmd finished after 0.019s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 2730672 bytes
Writing  time:   29.503s
Average write speed 348.7x.
Fixating...
Fixating time:    0.003s
/usr/bin/wodim: fifo had 235 puts and 44 gets.
/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 83%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdc speed=10 -dao textfile=/tmp/k3bebBRJa.dat -eject -useinfo -audio /tmp/kde-mike/k3b_audio_0_01.inf /tmp/kde-mike/k3b_audio_0_02.inf /tmp/kde-mike/k3b_audio_0_03.inf /tmp/kde-mike/k3b_audio_0_04.inf /tmp/kde-mike/k3b_audio_0_05.inf /tmp/kde-mike/k3b_audio_0_06.inf /tmp/kde-mike/k3b_audio_0_07.inf /tmp/kde-mike/k3b_audio_0_08.inf /tmp/kde-mike/k3b_audio_0_09.inf /tmp/kde-mike/k3b_audio_0_10.inf /tmp/kde-mike/k3b_audio_0_11.inf /tmp/kde-mike/k3b_audio_0_12.inf /tmp/kde-mike/k3b_audio_0_13.inf /tmp/kde-mike/k3b_audio_0_14.inf

---

### Post by slack31337 on 2008-02-16
i am using gutsy on one machine (cd r/w) and fiesty i think on the other (dvd r/w)

i have had a range of errors from permissions to fixation   

 i have used brasereo K3b nautaulis . My prefference is to get k3b to work as I am using KDE for now. 

Thanks for the quick replies

---

### Post by slack31337 on 2008-02-16
new info 

screen shot of error

[IMG]http://www.flickr.com/photos/slacking/2269722718/sizes/o/[/IMG]

[k3berror]("http://www.flickr.com/photos/slacking/2269722718/sizes/o")

and k3b output
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HP CD-Writer+ 9300 1.0b (/dev/hdc, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

K3bIsoImager
-----------------------
mkisofs print size result: 132489 (271337472 bytes)
Pipe throughput: 16435200 bytes read, 16430848 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'HP      '
Identification : 'CD-Writer+ 9300 '
Revision       : '1.0b'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 23805 kB/s 135x CD 17x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
Track 01: data   258 MB        
Total size:      297 MB (29:26.54) = 132491 sectors
Lout start:      297 MB (29:28/41) = 132491 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11080 (97:34/20)
  ATIP start of lead out: 335100 (74:30/00)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 335100 Blocks current: 335100 Blocks remaining: 202609
RBlocks total: 342460 RBlocks current: 342460 RBlocks remaining: 209969
Starting to write CD/DVD at speed  10.0 in real force TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  258 MB written.
Track 01:    1 of  258 MB written (fifo  98%) [buf  25%] 115.8x.
Track 01:    2 of  258 MB written (fifo  97%) [buf  51%] 120.7x.
Track 01:    3 of  258 MB written (fifo  99%) [buf  75%] 123.9x.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 07 DF 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 FF FF FF 6C 12 00 00 00 00 0C 08 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x08 (write error - recovery failed) Fru 0x0
Sense flags: Blk -148 (valid) 
resid: 63488
cmd finished after 2.803s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 4126720 bytes
Writing  time:   19.849s
Average write speed 219.5x.
Fixating...
Errno: 0 (Success), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.018s timeout 480s
cmd finished after 0.018s timeout 480s
Fixating time:    0.021s
/usr/bin/wodim: Cannot fixate disk.
/usr/bin/wodim: fifo had 257 puts and 66 gets.
/usr/bin/wodim: fifo was 0 times empty and 11 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdc speed=10 -tao -force -overburn -multi -xa -tsize=132489s - 

mkisofs
-----------------------
132489
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.39% done, estimate finish Sat Feb 16 14:19:44 2008
  0.76% done, estimate finish Sat Feb 16 14:19:44 2008
  1.13% done, estimate finish Sat Feb 16 14:19:44 2008
  1.52% done, estimate finish Sat Feb 16 14:19:44 2008
  1.90% done, estimate finish Sat Feb 16 14:19:44 2008
  2.27% done, estimate finish Sat Feb 16 14:19:44 2008
  2.64% done, estimate finish Sat Feb 16 14:19:44 2008
  3.03% done, estimate finish Sat Feb 16 14:19:44 2008
  3.40% done, estimate finish Sat Feb 16 14:19:44 2008
  3.78% done, estimate finish Sat Feb 16 14:19:44 2008
  4.15% done, estimate finish Sat Feb 16 14:19:44 2008
  4.54% done, estimate finish Sat Feb 16 14:19:44 2008
  4.91% done, estimate finish Sat Feb 16 14:24:49 2008
  5.29% done, estimate finish Sat Feb 16 14:24:27 2008
  5.66% done, estimate finish Sat Feb 16 14:24:08 2008
  6.05% done, estimate finish Sat Feb 16 14:23:51 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid et-linux-2.60.x86 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mike/k3blOtDna.tmp -rational-rock -hide-list /tmp/kde-mike/k3b3ZPBCa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-mike/k3b8cbUwb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-mike/k3bPvS6Va.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid et-linux-2.60.x86 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mike/k3bdZLf2a.tmp -rational-rock -hide-list /tmp/kde-mike/k3bTQwhta.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-mike/k3bYyQVCb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-mike/k3buJBenc.tmp

---

