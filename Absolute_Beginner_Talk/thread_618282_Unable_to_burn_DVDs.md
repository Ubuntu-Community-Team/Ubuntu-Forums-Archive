---
title: "Unable to burn DVDs"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by treacle boy on 2007-11-20
Hello all,

I am having some trouble burning DVDs on Gutsy Gibbon AMD64 (Ubuntu 7.10). I had a copy of Ubuntu Ultimate, which is based on Edgy, installed before and I was able to burn DVDs no problem. My processor is an AMD athlon 64 and the DVD drive that I am attempting to use is a Pioneer DVD-RW 108. I have tried 4 different methods of burning an .iso
[LIST=1]
[*]growisofs command
[*]K3b
[*]Nero for Linux 3
[*]Brasero
[/LIST]
The error messages that I got are shown below:
growisofs:
```
treacle@ubuntu:~/Dido 2007$ growisofs -dvd-compat -Z /dev/dvd=rld-di07.iso
Executing 'builtin_dd if=rld-di07.iso of=/dev/dvd obs=32k seek=0'
:-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
/dev/dvd: "Current Write Speed" is 12.3x1352KBps.
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-? the LUN appears to be stuck writing LBA=0h, keep retrying in 47ms
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2993258496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
```
the LUN continued to be stuck until I close the terminal down

K3b
```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-108 1.06 (/dev/hdd, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

PLEXTOR CD-R   PX-W1210A 1.05 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
:-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
/dev/hdd: "Current Write Speed" is 12.3x1352KBps.
    1605632/2993258496 ( 0.1%) @0.0x, remaining 155:16 RBU 100.0% UBU   2.0%
    1605632/2993258496 ( 0.1%) @0.0x, remaining 248:25 RBU 100.0% UBU 100.0%
:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms
    1605632/2993258496 ( 0.1%) @0.0x, remaining 341:35 RBU 100.0% UBU 100.0%
    1605632/2993258496 ( 0.1%) @0.0x, remaining 465:48 RBU 100.0% UBU 100.0%
    1605632/2993258496 ( 0.1%) @0.0x, remaining 558:58 RBU 100.0% UBU 100.0%
:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms
    1605632/2993258496 ( 0.1%) @0.0x, remaining 652:07 RBU 100.0% UBU 100.0%
    1605632/2993258496 ( 0.1%) @0.0x, remaining 776:20 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error
/dev/hdd: flushing cache
/dev/hdd: updating RMA
/dev/hdd: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1461552 -dvd-compat -speed=12 -use-the-force-luke=bufsize:32m 
```

I also noticed that when I started k3b form terminal I got this unhealthy looking messages:
```
treacle@ubuntu:~$ k3b
treacle@ubuntu:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_PIONEER_DVD_RW_DVR_108 to device /dev/hdd
Mapping udi /org/freedesktop/Hal/devices/storage_model_PLEXTOR_CD_R_PX_W1210A to device /dev/hdc
/dev/hdd resolved to /dev/hdd
/dev/hdd is block device (64)
/dev/hdd seems to be cdrom
(K3bDevice::Device) /dev/hdd: init()
(K3bDevice::Device) /dev/hdd feature: CD Mastering
(K3bDevice::Device) /dev/hdd feature: CD Track At Once
(K3bDevice::Device) /dev/hdd feature: DVD+R
(K3bDevice::Device) /dev/hdd feature: DVD+RW
(K3bDevice::Device) /dev/hdd feature: DVD+R Double Layer
(K3bDevice::Device) /dev/hdd feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/hdd feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/hdd: dataLen: 60
(K3bDevice::Device) /dev/hdd: checking for TAO
(K3bDevice::Device) /dev/hdd: checking for SAO
(K3bDevice::Device) /dev/hdd: checking for SAO_R96P
(K3bDevice::Device) /dev/hdd: checking for SAO_R96R
(K3bDevice::Device) /dev/hdd: checking for RAW_R16
(K3bDevice::Device) /dev/hdd: checking for RAW_R96P
(K3bDevice::Device) /dev/hdd: checking for RAW_R96R
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE dataLen = 136
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE successful with reported length: 132
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 8
(K3bDevice::Device) /dev/hdd : 22160 KB/s
(K3bDevice::Device) /dev/hdd : 16620 KB/s
(K3bDevice::Device) /dev/hdd : 11080 KB/s
(K3bDevice::Device) /dev/hdd : 8310 KB/s
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::Device) /dev/hdd : 3324 KB/s
(K3bDevice::Device) /dev/hdd : 2770 KB/s
(K3bDevice::Device) /dev/hdd : 1385 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdd to 22160
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdc: dataLen: 60
(K3bDevice::Device) /dev/hdc: checking for TAO
(K3bDevice::Device) /dev/hdc: checking for SAO
(K3bDevice::Device) /dev/hdc: checking for SAO_R96P
(K3bDevice::Device) /dev/hdc: checking for SAO_R96R
(K3bDevice::Device) /dev/hdc: checking for RAW_R16
(K3bDevice::Device) /dev/hdc: checking for RAW_R96P
(K3bDevice::Device) /dev/hdc: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        20
                           ascq:       0
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE length det failed.
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 0
/dev/hdd resolved to /dev/hdd
(K3bDevice::DeviceManager) dev /dev/hdd already found
/dev/hdc resolved to /dev/hdc
(K3bDevice::DeviceManager) dev /dev/hdc already found
(K3bDevice::DeviceManager) found config entry for devicetype: PIONEER DVD-RW  DVR-108
(K3bDevice::DeviceManager) found config entry for devicetype: PLEXTOR CD-R   PX-W1210A
Devices:
------------------------------
Blockdevice:    /dev/hdd
Generic device: 
Vendor:         PIONEER
Description:    DVD-RW  DVR-108
Version:        1.06
Write speed:    16620
Profiles:       DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/hdd
------------------------------
Blockdevice:    /dev/hdc
Generic device: 
Vendor:         PLEXTOR
Description:    CD-R   PX-W1210A
Version:        1.05
Write speed:    0
Profiles:       Error
Read Cap:       CD-ROM, CD-R, CD-RW
Write Cap:      CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R
Reader aliases: /dev/hdc
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
QGDict::hashKeyString: Invalid null key
QGDict::hashKeyString: Invalid null key
k3b: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol ''.
k3b: 
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 00:00:00 (LBA 0) (0 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 00:00:00 (LBA 0) (0 Bytes)
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:46:46 (LBA 2298496) (4707319808 Bytes)
Remaining size:  510:46:46 (LBA 2298496) (4707319808 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE dataLen = 72
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE successful with reported length: 68
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 4
(K3bDevice::Device) /dev/hdd : 16620 KB/s
(K3bDevice::Device) /dev/hdd : 11080 KB/s
(K3bDevice::Device) /dev/hdd : 8310 KB/s
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::Device) /dev/hdd: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/hdd: GET CONFIGURATION length det failed.
adding udi   /org/freedesktop/Hal/devices/volume_empty_dvd_r
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE dataLen = 72
(K3bDevice::Device) /dev/hdd: GET PERFORMANCE successful with reported length: 68
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 4
(K3bDevice::Device) /dev/hdd : 16620 KB/s
(K3bDevice::Device) /dev/hdd : 11080 KB/s
(K3bDevice::Device) /dev/hdd : 8310 KB/s
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_PIONEER_DVD_RW_DVR_108
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_PIONEER_DVD_RW_DVR_108
removing udi /org/freedesktop/Hal/devices/volume_empty_dvd_r

```

Nero for Linux 3
```
2CA0-7324-1800-2000-4077-1CEE-****

Linux 2.6.22-14-generic
Nero API version: 7.5.14.9
Using interface version: 7.5.1.2
Installed in: /usr/lib64/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 9

Recorder:             <PIONEER DVD-RW  DVR-108> Version: 1.06 - HA 0 TA 1 - 0.0.0.0
 Adapter driver:      <ide-cdrom>               HA 0
 Drive buffer  :      2000kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 73400320 (0) Byte
BUFE           : 0
Physical memory     : 500MB (512328kB)
Free physical memory: 73MB (75504kB)
Memory in use       : 85 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

19.11.2007
NeroAPI
12:52:04	#1 Phase 114 File ExtendedProgress.cpp, Line 537
	DVD-Video files reallocation completed (no file modified)
	
12:52:05	#2 Phase 111 File ExtendedProgress.cpp, Line 537
	DVD-Video files sorted
	
12:52:05	#3 ISO9660GEN -11 File Geniso.cpp, Line 3341
	First writeable address = 0 (0x00000000)
	
12:52:06	#4 ISO9660GEN -11 File Geniso.cpp, Line 3341
	First writeable address = 0 (0x00000000)
	
12:52:06	#5 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using DVD media
	
12:52:07	#6 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2298495 (510:46.45, 4489MB)
	Last address to be written:            1190239 (264:29.64, 2324MB)
	
12:52:07	#7 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
12:52:07	#8 Text 0 File DlgWaitCD.cpp, Line 2952
	Recorder: PIONEER DVD-RW  DVR-108, Media type: DVD-R
	 Disc Manufacturer: RITEKG - 05
	 Disc Application Code: 64, Disc Physical Code: 193
	
12:52:07	#9 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
12:52:07	#10 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 ()
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 1190240 (1190240) = #1190240/264:29.65
	    relocatable, disc pos for caching/writing not required/ required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 1190240 blocks [PIONEER DVD-RW  DVR-108 (H:0 T:1)]
	--------------------------------------------------------------
	
12:52:07	#11 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [PIONEER DVD-RW  DVR-108 (H:0 T:1)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    2437611520, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  1190240 |        0 | 0x00
	  1190240 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
12:52:07	#12 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
12:52:07	#13 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
12:52:07	#14 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
12:52:07	#15 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
12:52:07	#16 Phase 28 File ExtendedProgress.cpp, Line 537
	Speed measurement started
	
12:52:07	#17 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
12:52:07	#18 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 590400
	
12:53:47	#19 Text 0 File WriterStatus.cpp, Line 113
	<PIONEER DVD-RW  DVR-108 (H:0 T:1)> start writing Lead-Out at LBA 1190240 (122960h), length 0 blocks
	
12:53:47	#20 Phase 29 File ExtendedProgress.cpp, Line 470
	Speed measurement completed: 17.3x (23996 KB/s)
	
12:53:47	#21 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 4x (5540 KB/s)
	
12:53:47	#22 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
12:53:47	#23 Text 0 File DVDR.cpp, Line 3159
	Recording mode: Sequential Recording Mode
	
12:53:47	#24 Text 0 File DVDR.cpp, Line 3315
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
12:53:47	#25 Text 0 File Cdrdrv.cpp, Line 9915
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 0.0 (0)
	 Disc Size: 120 mm,      Maximum Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Sector Number in Layer 0:                 0 h (LBN: FFFD0000 h, 4193920 MB)
	 Data in Burst Cutting Area (BCA) does not exist
	  Revision number of maximum recording speed: 3.0
	  Revision number of minimum recording speed: 0.0
	  Revision number table of recording speed: 0.1 0.2 0.3 - - - 0.4 
	  Class: 0
	  Start sector number of the current Border-Out: 0 h
	  Start sector number of the next Border-In:     0 h
	 Media Specific [16..63]:
	    00 30 01 02 04 06 00 00 - 00 08 00 00 00 00 00 00    .0..............
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
12:53:47	#26 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 73340800
	
12:53:48	#27 Text 0 File Cdrdrv.cpp, Line 1348
	12:53:48 - PIONEER DVD-RW  DVR-108 (H:0 T:1) : Queue again later
	
12:54:01	#28 SCSI -1061 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 0, TA 1, LUN 0, buffer 0x0x2aaab30e4640
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x02 (0x01, SCSI_TASTATUS_CHKCOND)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x44
	Sense Qual: 0xD9
	CDB Data:   0x2A 0x00 0x00 0x00 0x03 0x00 0x00 0x00 0x20 0x00 0x00 0x00 
	Sense Data: 0x71 0x00 0x04 0x00 0x00 0x00 0x00 0x0E 
	            0x00 0x00 0x00 0x00 0x44 0xD9 
	
12:54:01	#29 CDR -1061 File Writer.cpp, Line 299
	Internal target failure
	PIONEER DVD-RW  DVR-108 (H:0 T:1)
	
12:54:01	#30 Text 0 File DVDR.cpp, Line 3717
	EndDAO: Last written address was 767 (2FFh)
	
12:54:01	#31 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 4x (5540 KB/s)
	
```

Brasero
```
imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8535 
	media type	= 0
	speed		= 0
	track type		= 8
	track format	= 2
	output		= none
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/hdd=/home/jim/Fifa 2007/rld-fi07.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/home/jim/Fifa 2007/rld-fi07.iso of=/dev/hdd obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/hdd: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: :-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
process (BraseroGrowisofs) stderr: /dev/hdd: reserving 1461552 blocks
process (BraseroGrowisofs) stderr: /dev/hdd: "Current Write Speed" is 4.1x1352KBps.
process (BraseroGrowisofs) stdout:     1605632/2993258496 ( 0.1%) @0.0x, remaining 155:16 RBU 100.0% UBU   2.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:     1605632/2993258496 ( 0.1%) @0.0x, remaining 248:25 RBU 100.0% UBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting
```

Following this link [http://pcburn.com/article.php?sid=2127](http://pcburn.com/article.php?sid=2127) I have found that the SK=4h/ASC=44h/ACQ=D9h error message means "4 44 00 INTERNAL TARGET FAILURE" (if my hex translation is right!) this unfortunately leaves me none the wiser. 

My present theory is that this:
(K3bDevice::ScsiCommand) failed
means that I should be running the drive as a Scsi emulated one, which is something I had to do when I was running Breezy Badger. 

Another theory is that the "dvd+rw-tools" which appears to contain the growisofs package in Gutsy has one which is incompatible with my set up, so I was thinking of down grading it to the version that comes with Edgy, does anyone know what this is called and where I can get it? And if it is wise to do such a thing?!

Any help appreciated,

Treacle Boy

---

### Post by gupta_sumesh63 on 2007-11-20
I had a similar problem while burning a CD. I tried with all the available applications. However it failed.
I tried with a new Disk and it worked.
I believe these messages show when the disk is bad. try using a fresh disk. It should burn.

---

### Post by treacle boy on 2007-11-22
Thanks Gupta,

I managed to burn my DVD in the end you will be pleased to hear. First I cleaned the lens then I used a better quality of media (Maxwell are much better than Tesco value - surprise, surprise)

---

### Post by Paul820 on 2007-11-22
I would not trust my data on Tesco value CD's. Good quality CD/DVD's are much more reliable and less error prone to bad burns.

---

