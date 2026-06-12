---
title: "CD's won't burn"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by sirzepp on 2008-01-23
I've searched the forums and I have turned on DMA, tried using cdrecord with the -raw96r option, and I still can't burn cds.  All cd/dvd software fails from cdrecord(at the cmd line) to Brasero and Nero(even bought Nero).  After having this difficulty, I bought a new DVD/CD writer...and cd burning still doesn't work.  It's not a hardware problem, as I've tried 2 different CD writers.  Both of them worked in Windows.

Here is my brasero log file:

[INDENT]mager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8535 
	media type	= 0
	speed		= 47
	track type		= 8
	track format	= 2
	output		= none
job (BraseroCDRecord) set_rate
recorder (BraseroCDRecord) set_drive
recorder (BraseroCDRecord) set_flags
job (BraseroCDRecord) set_source
job (BraseroCDRecord) set_task
recorder (BraseroCDRecord) record
process (BraseroCDRecord) getting varg
cdrecord (BraseroCDRecord) set_action
process (BraseroCDRecord) got varg:
	/usr/bin/wodim
	-v
	dev=/dev/scd0
	gracetime=0
	speed=47
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/sirzepp/Desktop/gparted-livecd-0.3.4-11.iso
process (BraseroCDRecord) launching command
process (BraseroCDRecord) stderr: /usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
process (BraseroCDRecord) stderr: devname: '/dev/scd0'
process (BraseroCDRecord) stderr: scsibus: -2 target: -2 lun: -2
process (BraseroCDRecord) stderr: Linux sg driver version: 3.5.27
process (BraseroCDRecord) stderr: Wodim version: 1.1.6
process (BraseroCDRecord) stderr: SCSI buffer size: 64512
process (BraseroCDRecord) stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
process (BraseroCDRecord) stderr: communication breaks or freezes immediately after that.
process (BraseroCDRecord) stdout: TOC Type: 1 = CD-ROM
process (BraseroCDRecord) stdout: Driveropts: 'burnfree'
process (BraseroCDRecord) stdout: Device type    : Removable CD-ROM
process (BraseroCDRecord) stdout: Version        : 5
process (BraseroCDRecord) stdout: Response Format: 2
process (BraseroCDRecord) stdout: Capabilities   : 
process (BraseroCDRecord) stdout: Vendor_info    : 'PIONEER '
process (BraseroCDRecord) stdout: Identification : 'DVD-RW  DVR-212D'
process (BraseroCDRecord) stdout: Revision       : '1.21'
process (BraseroCDRecord) stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
process (BraseroCDRecord) stdout: Current: 0x0009 (CD-R)
process (BraseroCDRecord) stdout: Profile: 0x002B (DVD+R/DL) 
process (BraseroCDRecord) stdout: Profile: 0x001B (DVD+R) 
process (BraseroCDRecord) stdout: Profile: 0x001A (DVD+RW) 
process (BraseroCDRecord) stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
process (BraseroCDRecord) stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0014 (DVD-RW sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
process (BraseroCDRecord) stdout: Profile: 0x0011 (DVD-R sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0010 (DVD-ROM) 
process (BraseroCDRecord) stdout: Profile: 0x000A (CD-RW) 
process (BraseroCDRecord) stdout: Profile: 0x0009 (CD-R) (current)
process (BraseroCDRecord) stdout: Profile: 0x0008 (CD-ROM) 
process (BraseroCDRecord) stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
process (BraseroCDRecord) stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
process (BraseroCDRecord) stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
process (BraseroCDRecord) stdout: Drive buf size : 1267712 = 1238 KB
process (BraseroCDRecord) stdout: FIFO size      : 16777216 = 16384 KB
process (BraseroCDRecord) stderr: Speed set to 7056 KB/s
process (BraseroCDRecord) stdout: Track 01: data    52 MB        
process (BraseroCDRecord) stdout: Total size:       59 MB (05:55.37) = 26653 sectors
process (BraseroCDRecord) stdout: Lout start:       60 MB (05:57/28) = 26653 sectors
process (BraseroCDRecord) stdout: Current Secsize: 2048
process (BraseroCDRecord) stdout: ATIP info from disk:
process (BraseroCDRecord) stdout:   Indicated writing power: 5
process (BraseroCDRecord) stdout:   Is not unrestricted
process (BraseroCDRecord) stdout:   Is not erasable
process (BraseroCDRecord) stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
process (BraseroCDRecord) stdout:   ATIP start of lead in:  -11634 (97:26/66)
process (BraseroCDRecord) stdout:   ATIP start of lead out: 359846 (79:59/71)
process (BraseroCDRecord) stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
process (BraseroCDRecord) stdout: Manuf. index: 3
process (BraseroCDRecord) stdout: Manufacturer: CMC Magnetics Corporation
process (BraseroCDRecord) stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 333193
process (BraseroCDRecord) stdout: Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
process (BraseroCDRecord) stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
process (BraseroCDRecord) stdout: Waiting for reader process to fill input buffer ... input buffer ready.
process (BraseroCDRecord) stdout: Performing OPC...
process (BraseroCDRecord) stdout: Sending CUE sheet...
process (BraseroCDRecord) set_action
process (BraseroCDRecord) stderr: /usr/bin/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
process (BraseroCDRecord) stderr: Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
process (BraseroCDRecord) stderr: CDB:  5D 00 00 00 00 00 00 00 20 00
process (BraseroCDRecord) stderr: status: 0x2 (CHECK CONDITION)
process (BraseroCDRecord) stderr: Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 10 40 A8 04 00 00
process (BraseroCDRecord) stderr: Sense Key: 0x5 Illegal Request, Segment 0
process (BraseroCDRecord) stderr: Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
process (BraseroCDRecord) stderr: Sense flags: Blk 100663328 (not valid) 
process (BraseroCDRecord) stderr: cmd finished after 0.019s timeout 200s
process (BraseroCDRecord) stderr: /usr/bin/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
process (BraseroCDRecord) stderr: /usr/bin/wodim: Cannot send CUE sheet.
process (BraseroCDRecord) stderr: /usr/bin/wodim: Could not write Lead-in.
job (BraseroCDRecord) asked to stop
	status	= 1
	error		= 1
	message	= "the cd information could not be written"
iter (BraseroCDRecord) stopping
process (BraseroCDRecord) got killed
iter (BraseroCDRecord) stopped
job (BraseroCDRecord) got out of loop
job (BraseroCDRecord) set_task
Session error : the cd information could not be written[/INDENT]

Here is my Nero log file:

[INDENT]2CA0-80X3-1800-2000-406M-AA2A-****

Linux 2.6.22-14-generic
Nero API version: 7.5.14.4
Using interface version: 7.5.0.2
Installed in: /usr/lib64/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 4

Recorder:             <PIONEER DVD-RW  DVR-212D>Version: 1.21 - HA 4 TA 0 - 0.0.0.0
 Adapter driver:      <sata_via>                HA 4
 Drive buffer  :      2000kB
 Bus Type      :      default (0) -> SCSI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1004MB (1028720kB)
Free physical memory: 339MB (347556kB)
Memory in use       : 66 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

23.1.2008
NeroAPI
05:20:22 PM	#1 Text 0 File Burncd.cpp, Line 3178
	PIONEER DVD-RW  DVR-212D
	Buffer underrun protection activated
	
05:20:23 PM	#2 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using CD-R/RW media
	
05:20:33 PM	#3 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:   359845 ( 79:59.70)
	Last address to be written:              26652 (  5:57.27)
	
05:20:33 PM	#4 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
05:20:33 PM	#5 Text 0 File DlgWaitCD.cpp, Line 2951
	Recorder: PIONEER DVD-RW  DVR-212D;
	   CDR code: 00 97 26 66; OSJ entry from: CMC Magnetics Corporation
	   ATIP Data:
	     Special    Info [hex] 1: D0 00 98, 2: 61 1A 42 (LI 97:26.66), 3: 4F 3B 47 (LO 79:59.71)
	     Additional Info [hex] 1: FF FF FF (invalid), 2: FF FF FF (invalid), 3: FF FF FF (invalid)
	
05:20:33 PM	#6 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
05:20:33 PM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 26653 (26653) = #26653/5:55.28
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_ULTRARAW96_MODE1, 2448, config 4, wanted index0 0 blocks, length 26653 blocks [PIONEER DVD-RW  DVR-212D (H:4 T:0)]
	--------------------------------------------------------------
	
05:20:33 PM	#8 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [PIONEER DVD-RW  DVR-212D (H:4 T:0)] for write in raw writing
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_ULTRARAW96_MODE1, 2448/0x04, FilePos             0        367200      65613744, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |    26653 |    26653 | 0x00
	    26653 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
05:20:33 PM	#9 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
05:20:33 PM	#10 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
05:20:33 PM	#11 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
05:20:33 PM	#12 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
05:20:33 PM	#13 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 40x (6000 KB/s)
	
05:20:33 PM	#14 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
05:20:33 PM	#15 Text 0 File MMC.cpp, Line 17730
	StartDAO : CD-Text - Off
	
05:20:33 PM	#16 Text 0 File MMC.cpp, Line 22396
	Set BUFE: Buffer underrun protection -> ON 
	
05:20:33 PM	#17 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
05:20:34 PM	#18 SCSI -400 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 4, TA 0, LUN 0, buffer 0x0x15a9ec0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0xA8
	Sense Qual: 0x04
	CDB Data:   0x2A 0x00 0xFF 0xFF 0xD2 0x8E 0x00 0x00 0x1A 0x00 
	Sense Data: 0x70 0x00 0x05 0x06 0x00 0x00 0x20 0x0E 
	            0x24 0x08 0x10 0x40 0xA8 0x04 
	
05:20:34 PM	#19 CDR -400 File Writer.cpp, Line 299
	Unspecified target error
	PIONEER DVD-RW  DVR-212D (H:4 T:0)
	
05:20:35 PM	#20 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 40x (6000 KB/s)
	[/INDENT]

As you can see, both fail.  The Brasero failure is similar to the message I got with cdrecord in that it "failed to send the CUE sheet".  Please help!  I am really enjoying Ubuntu, but having to boot windows to burn CD's is a bummer.

thanks!

Jimmy Page(no, not that one).

---

### Post by disturbed1 on 2008-01-23
The SCSI errors reported seem like media errors.

Your firmware is at v 1.21, the newest version for the Pioneer DVR-212D is v 1.24 with this noted in the change log - CD-R Writability has improved. -

The download page is here
[http://www.pioneer.eu/eur/content/support/support/software.html#fdvdwriter](http://www.pioneer.eu/eur/content/support/support/software.html#fdvdwriter)

---

### Post by sirzepp on 2008-01-23
Thanks, I'll give that a try.

---

### Post by sirzepp on 2008-01-23
OK, I updated my firmware.

Same result.

Here is the new nero log file:

[INDENT]2CA0-80X3-1800-2000-406M-AA2A-****

Linux 2.6.22-14-generic
Nero API version: 7.5.14.4
Using interface version: 7.5.0.2
Installed in: /usr/lib64/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 4

Recorder:             <PIONEER DVD-RW  DVR-212D>Version: 1.24 - HA 4 TA 0 - 0.0.0.0
 Adapter driver:      <sata_via>                HA 4
 Drive buffer  :      2000kB
 Bus Type      :      default (0) -> SCSI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1509MB (1545812kB)
Free physical memory: 842MB (863112kB)
Memory in use       : 44 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

23.1.2008
NeroAPI
08:25:18 PM	#1 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:   359845 ( 79:59.70)
	Last address to be written:              26652 (  5:57.27)
	
08:25:18 PM	#2 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
08:25:18 PM	#3 Text 0 File DlgWaitCD.cpp, Line 2951
	Recorder: PIONEER DVD-RW  DVR-212D;
	   CDR code: 00 97 26 66; OSJ entry from: CMC Magnetics Corporation
	   ATIP Data:
	     Special    Info [hex] 1: D0 00 98, 2: 61 1A 42 (LI 97:26.66), 3: 4F 3B 47 (LO 79:59.71)
	     Additional Info [hex] 1: FF FF FF (invalid), 2: FF FF FF (invalid), 3: FF FF FF (invalid)
	
08:25:18 PM	#4 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
08:25:18 PM	#5 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 26653 (26653) = #26653/5:55.28
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_ULTRARAW96_MODE1, 2448, config 4, wanted index0 0 blocks, length 26653 blocks [PIONEER DVD-RW  DVR-212D (H:4 T:0)]
	--------------------------------------------------------------
	
08:25:20 PM	#6 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [PIONEER DVD-RW  DVR-212D (H:4 T:0)] for write in raw writing
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_ULTRARAW96_MODE1, 2448/0x04, FilePos             0        367200      65613744, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |    26653 |    26653 | 0x00
	    26653 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
08:25:20 PM	#7 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
08:25:20 PM	#8 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
08:25:20 PM	#9 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
08:25:20 PM	#10 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
08:25:20 PM	#11 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 40x (6000 KB/s)
	
08:25:21 PM	#12 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
08:25:21 PM	#13 Text 0 File MMC.cpp, Line 17730
	StartDAO : CD-Text - Off
	
08:25:21 PM	#14 Text 0 File MMC.cpp, Line 22396
	Set BUFE: Buffer underrun protection -> ON 
	
08:25:21 PM	#15 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
08:25:22 PM	#16 SCSI -400 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 4, TA 0, LUN 0, buffer 0x0x15d6cc0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0xA8
	Sense Qual: 0x04
	CDB Data:   0x2A 0x00 0xFF 0xFF 0xD2 0x8E 0x00 0x00 0x1A 0x00 
	Sense Data: 0x70 0x00 0x05 0x06 0x00 0x00 0x20 0x0E 
	            0x24 0x08 0x11 0x40 0xA8 0x04 
	
08:25:22 PM	#17 CDR -400 File Writer.cpp, Line 299
	Unspecified target error
	PIONEER DVD-RW  DVR-212D (H:4 T:0)
	
08:25:22 PM	#18 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 40x (6000 KB/s)
	[/INDENT]

What is going on?

My machine config is:

ASUS K8N+ MB
AMD Athlon 64 2800+
1.5 GB of RAM
System Disk: 15GB/8.2 GB free (IDE Channel 2 Slave)
Optical Drive 1: 52x CD-ROM(IDE Channel 1 Master)
Optical Drive 2: Pioneer DVR-212D (SATA)
NTFS Disk 1: 52GB (IDE Channel 1 Master)
NTFS Disk 2: 120GB (IDE Channel 1 Slave)
Geforce 440MX 64MB AGP Video Card
Atheros Wireless(D-link)

---

### Post by sirzepp on 2008-01-23
Here is my latest Brasero log:

imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8535 
	media type	= 0
	speed		= 47
	track type		= 8
	track format	= 2
	output		= none
job (BraseroCDRecord) set_rate
recorder (BraseroCDRecord) set_drive
recorder (BraseroCDRecord) set_flags
job (BraseroCDRecord) set_source
job (BraseroCDRecord) set_task
recorder (BraseroCDRecord) record
process (BraseroCDRecord) getting varg
cdrecord (BraseroCDRecord) set_action
process (BraseroCDRecord) got varg:
	/usr/bin/wodim
	-v
	dev=/dev/scd0
	gracetime=0
	speed=47
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/sirzepp/Desktop/gparted-livecd-0.3.4-11.iso
process (BraseroCDRecord) launching command
process (BraseroCDRecord) stderr: /usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
process (BraseroCDRecord) stderr: devname: '/dev/scd0'
process (BraseroCDRecord) stderr: scsibus: -2 target: -2 lun: -2
process (BraseroCDRecord) stderr: Linux sg driver version: 3.5.27
process (BraseroCDRecord) stderr: Wodim version: 1.1.6
process (BraseroCDRecord) stderr: SCSI buffer size: 64512
process (BraseroCDRecord) stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
process (BraseroCDRecord) stderr: communication breaks or freezes immediately after that.
process (BraseroCDRecord) stdout: TOC Type: 1 = CD-ROM
process (BraseroCDRecord) stdout: Driveropts: 'burnfree'
process (BraseroCDRecord) stdout: Device type    : Removable CD-ROM
process (BraseroCDRecord) stdout: Version        : 5
process (BraseroCDRecord) stdout: Response Format: 2
process (BraseroCDRecord) stdout: Capabilities   : 
process (BraseroCDRecord) stdout: Vendor_info    : 'PIONEER '
process (BraseroCDRecord) stdout: Identification : 'DVD-RW  DVR-212D'
process (BraseroCDRecord) stdout: Revision       : '1.24'
process (BraseroCDRecord) stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
process (BraseroCDRecord) stdout: Current: 0x0009 (CD-R)
process (BraseroCDRecord) stdout: Profile: 0x002B (DVD+R/DL) 
process (BraseroCDRecord) stdout: Profile: 0x001B (DVD+R) 
process (BraseroCDRecord) stdout: Profile: 0x001A (DVD+RW) 
process (BraseroCDRecord) stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
process (BraseroCDRecord) stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0014 (DVD-RW sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
process (BraseroCDRecord) stdout: Profile: 0x0011 (DVD-R sequential recording) 
process (BraseroCDRecord) stdout: Profile: 0x0010 (DVD-ROM) 
process (BraseroCDRecord) stdout: Profile: 0x000A (CD-RW) 
process (BraseroCDRecord) stdout: Profile: 0x0009 (CD-R) (current)
process (BraseroCDRecord) stdout: Profile: 0x0008 (CD-ROM) 
process (BraseroCDRecord) stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
process (BraseroCDRecord) stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
process (BraseroCDRecord) stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
process (BraseroCDRecord) stdout: Drive buf size : 1267712 = 1238 KB
process (BraseroCDRecord) stdout: FIFO size      : 16777216 = 16384 KB
process (BraseroCDRecord) stderr: Speed set to 7056 KB/s
process (BraseroCDRecord) stdout: Track 01: data    52 MB        
process (BraseroCDRecord) stdout: Total size:       59 MB (05:55.37) = 26653 sectors
process (BraseroCDRecord) stdout: Lout start:       60 MB (05:57/28) = 26653 sectors
process (BraseroCDRecord) stdout: Current Secsize: 2048
process (BraseroCDRecord) stdout: ATIP info from disk:
process (BraseroCDRecord) stdout:   Indicated writing power: 5
process (BraseroCDRecord) stdout:   Is not unrestricted
process (BraseroCDRecord) stdout:   Is not erasable
process (BraseroCDRecord) stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
process (BraseroCDRecord) stdout:   ATIP start of lead in:  -11634 (97:26/66)
process (BraseroCDRecord) stdout:   ATIP start of lead out: 359846 (79:59/71)
process (BraseroCDRecord) stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
process (BraseroCDRecord) stdout: Manuf. index: 3
process (BraseroCDRecord) stdout: Manufacturer: CMC Magnetics Corporation
process (BraseroCDRecord) stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 333193
process (BraseroCDRecord) stdout: Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
process (BraseroCDRecord) stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
process (BraseroCDRecord) stdout: Waiting for reader process to fill input buffer ... input buffer ready.
process (BraseroCDRecord) stdout: Performing OPC...
process (BraseroCDRecord) stdout: Sending CUE sheet...
process (BraseroCDRecord) set_action
process (BraseroCDRecord) stderr: /usr/bin/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
process (BraseroCDRecord) stderr: Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
process (BraseroCDRecord) stderr: CDB:  5D 00 00 00 00 00 00 00 20 00
process (BraseroCDRecord) stderr: status: 0x2 (CHECK CONDITION)
process (BraseroCDRecord) stderr: Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 11 40 A8 04 00 00
process (BraseroCDRecord) stderr: Sense Key: 0x5 Illegal Request, Segment 0
process (BraseroCDRecord) stderr: Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
process (BraseroCDRecord) stderr: Sense flags: Blk 100663328 (not valid) 
process (BraseroCDRecord) stderr: cmd finished after 0.019s timeout 200s
process (BraseroCDRecord) stderr: /usr/bin/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
process (BraseroCDRecord) stderr: /usr/bin/wodim: Cannot send CUE sheet.
process (BraseroCDRecord) stderr: /usr/bin/wodim: Could not write Lead-in.
job (BraseroCDRecord) asked to stop
	status	= 1
	error		= 1
	message	= "the cd information could not be written"
iter (BraseroCDRecord) stopping
process (BraseroCDRecord) got killed
iter (BraseroCDRecord) stopped
job (BraseroCDRecord) got out of loop
job (BraseroCDRecord) set_task
Session error : the cd information could not be written

Like I said, firmware is up to date
I'm getting the same errors no matter what software I use.
Both drives I've tried work flawlessy under windows.

---

### Post by Lostincyberspace on 2008-01-23
Have you tried running it through k3b?

---

### Post by sirzepp on 2008-01-24
I've tried all of the programs in the first post...I'll install and try k3b...I don't think it will work as cdrecord is used by k3b, isn't it?  If cdrecord won't work from the command line, it won't work here...but here we go

---

### Post by sirzepp on 2008-01-24
K3b output as follows:



System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
CD-ROM CCD-52X6S YS0C (/dev/hdb, ) [CD-ROM] [Error] [None]

PIONEER DVD-RW  DVR-212D 1.24 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-212D'
Revision       : '1.24'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 7056 KB/s
Track 01: data    52 MB        
Total size:       59 MB (05:55.37) = 26653 sectors
Lout start:       60 MB (05:57/28) = 26653 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 333193
Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 11 40 A8 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
Sense flags: Blk 100663328 (not valid) 
cmd finished after 0.021s timeout 200s
/usr/bin/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/wodim: Cannot send CUE sheet.
/usr/bin/wodim: Could not write Lead-in.
Writing  time:   18.448s
/usr/bin/wodim: fifo had 191 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=40 -dao driveropts=burnfree -eject -data -tsize=26653s -

---

### Post by sirzepp on 2008-01-24
As you can see, it can't send the CUE sheet...whatever that is.

This is the same error I got with my previous drive...so, again, it's not a hardware problem.
And again, these drives both work in windows.

---

### Post by sirzepp on 2008-01-24
Here is a K3b log from an attempt to burn an audio CD:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
CD-ROM CCD-52X6S YS0C (/dev/hdb, ) [CD-ROM] [Error] [None]

PIONEER DVD-RW  DVR-212D 1.24 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
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
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-212D'
Revision       : '1.24'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   33 MB (03:21.57) no preemp swab copy
Track 02: audio   46 MB (04:37.64) no preemp swab copy
Track 03: audio   41 MB (04:06.52) no preemp swab copy
Track 04: audio   39 MB (03:57.09) no preemp swab copy
Track 05: audio   44 MB (04:23.26) no preemp swab copy
Track 06: audio   50 MB (04:57.25) no preemp swab copy
Track 07: audio   44 MB (04:22.48) no preemp swab copy
Track 08: audio   37 MB (03:44.24) no preemp swab copy
Track 09: audio   29 MB (02:53.06) no preemp swab copy
Track 10: audio   39 MB (03:57.36) no preemp swab copy
Track 11: audio   46 MB (04:38.16) no preemp swab copy
Track 12: audio   56 MB (05:36.44) no preemp swab copy
Track 13: audio   19 MB (01:54.32) no preemp swab copy
Track 14: audio   96 MB (09:33.10) no preemp swab copy
Total size:      626 MB (62:02.52) = 279189 sectors
Lout start:      626 MB (62:04/39) = 279189 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
Speed set to 5644 KB/s
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 80657
Starting to write CD/DVD at speed  32.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 F0 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 11 40 A8 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
Sense flags: Blk 100663328 (not valid) 
cmd finished after 0.019s timeout 200s
/usr/bin/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/wodim: Cannot send CUE sheet.
/usr/bin/wodim: Could not write Lead-in.
Writing  time:   18.146s
/usr/bin/wodim: fifo had 191 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=32 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-sirzepp/k3b_audio_0_01.inf /tmp/kde-sirzepp/k3b_audio_0_02.inf /tmp/kde-sirzepp/k3b_audio_0_03.inf /tmp/kde-sirzepp/k3b_audio_0_04.inf /tmp/kde-sirzepp/k3b_audio_0_05.inf /tmp/kde-sirzepp/k3b_audio_0_06.inf /tmp/kde-sirzepp/k3b_audio_0_07.inf /tmp/kde-sirzepp/k3b_audio_0_08.inf /tmp/kde-sirzepp/k3b_audio_0_09.inf /tmp/kde-sirzepp/k3b_audio_0_10.inf /tmp/kde-sirzepp/k3b_audio_0_11.inf /tmp/kde-sirzepp/k3b_audio_0_12.inf /tmp/kde-sirzepp/k3b_audio_0_13.inf /tmp/kde-sirzepp/k3b_audio_0_14.inf

---

### Post by sirzepp on 2008-01-24
Here is a K3b log after trying TAO instead of DAO

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
CD-ROM CCD-52X6S YS0C (/dev/hdb, ) [CD-ROM] [Error] [None]

PIONEER DVD-RW  DVR-212D 1.24 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-212D'
Revision       : '1.24'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   33 MB (03:21.57) no preemp swab copy
Track 02: audio   46 MB (04:37.64) no preemp swab copy
Track 03: audio   41 MB (04:06.52) no preemp swab copy
Track 04: audio   39 MB (03:57.09) no preemp swab copy
Track 05: audio   44 MB (04:23.26) no preemp swab copy
Track 06: audio   50 MB (04:57.25) no preemp swab copy
Track 07: audio   44 MB (04:22.48) no preemp swab copy
Track 08: audio   37 MB (03:44.24) no preemp swab copy
Track 09: audio   29 MB (02:53.06) no preemp swab copy
Track 10: audio   39 MB (03:57.36) no preemp swab copy
Track 11: audio   46 MB (04:38.16) no preemp swab copy
Track 12: audio   56 MB (05:36.44) no preemp swab copy
Track 13: audio   19 MB (01:54.32) no preemp swab copy
Track 14: audio   96 MB (09:33.10) no preemp swab copy
Total size:      630 MB (62:28.52) = 281139 sectors
Lout start:      630 MB (62:30/39) = 281139 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 78707
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 7056 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   33 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 11 40 A8 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
Sense flags: Blk 100663328 (not valid) 
cmd finished after 0.083s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   19.662s
Average write speed 707.8x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.007s timeout 480s
cmd finished after 0.007s timeout 480s
Fixating time:    0.012s
/usr/bin/wodim: Cannot fixate disk.
/usr/bin/wodim: fifo had 191 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=40 -tao driveropts=burnfree -eject -useinfo -audio /tmp/kde-sirzepp/k3b_audio_0_01.inf /tmp/kde-sirzepp/k3b_audio_0_02.inf /tmp/kde-sirzepp/k3b_audio_0_03.inf /tmp/kde-sirzepp/k3b_audio_0_04.inf /tmp/kde-sirzepp/k3b_audio_0_05.inf /tmp/kde-sirzepp/k3b_audio_0_06.inf /tmp/kde-sirzepp/k3b_audio_0_07.inf /tmp/kde-sirzepp/k3b_audio_0_08.inf /tmp/kde-sirzepp/k3b_audio_0_09.inf /tmp/kde-sirzepp/k3b_audio_0_10.inf /tmp/kde-sirzepp/k3b_audio_0_11.inf /tmp/kde-sirzepp/k3b_audio_0_12.inf /tmp/kde-sirzepp/k3b_audio_0_13.inf /tmp/kde-sirzepp/k3b_audio_0_14.inf

---

### Post by sirzepp on 2008-01-24
Has anyone solved this problem?

---

### Post by disturbed1 on 2008-01-24
This issue is quite strange. It would be easy to blame wodim since it's a hack of cdrecord's 2004 code and has many out standing bugs, but Nero has the same problem, yet it uses it's own burning library.

The only thing that comes to mind is a problem with Linux using SATA burners. Which is an old known problem with Wodim and should have been fixed some time ago, Perhaps Nero too?


Other advice I have to offer, is to use a legit copy of cdrecord (available in Synaptic) and try that. The REAL cdrecord has had this bug fixed. The version in Synaptic is not the newest of new, but does include this bug fix.  2.01.01a33 (08/12/2007) is in Synaptic, 2.01.01a37 (01/02/2008 ) is the newest. So it's not too old ;)

If this still fails, I'd file a bug at Launchpad.net. Even if cdrecord fixes the issue, I'd still file a bug against wodim.

---

### Post by sirzepp on 2008-01-24
Thanks!  I'll load the cdrecord off synaptic(I think I alread did, but I make sure) and file a bug against wodim.  So SATA burner support is spotty in Linux or spotty in Ubuntu?  I guess what I'm asking is, if I go to 32bit Ubuntu or MEPIS will it work better?  I may just go dig my old IDE drive up and use that...and just wait for an update to burn DVDs in Linux on my SATA drive;).

---

### Post by sirzepp on 2008-01-24
OK I have the synaptic version of cdrecord on my machine and even at the command line it won't work unless I use the -raw96r option and even then I get a coaster.  SO I'll file a bug report and return my new SATA drive and pick up an IDE DVD/CDR...hopefully that solves it. I'll just use my old SATA CD-burner as my secondary CD-ROM...since linux reads the SATA disks fine, it just can't seem to write to them.

---

### Post by disturbed1 on 2008-01-24
Deleted after reply.

---

### Post by sirzepp on 2008-01-24
Thanks for your help, disturbed1, I'll report back after I install the IDE drive.

---

### Post by disturbed1 on 2008-01-24
I found some info,

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)
> 
** Problem burning CD/DVD**

 To a CD/DVD problem, try to burn a CD/DVD as "root"-user on command-line with the option "-dummy" and "-v" enabled, do not use K3B or similar. Doing so you will get more informations and waste less CD/DVD's. 
Experiment with the parameters "burnfree" and "dev". With cdrecord on debian etch, burnfree seems not work, disable it. With wodim on debian etch: try parameter "dev=/dev/scd0", the default "dev=1,0,0" seems not to work.



Also, if your BIOS allows PATA emulation for the drive, you may want to give that a shot. I'd hate to see you not able to use your drive.

As far using 32bit instead, I'd boot the Live CD, and try to burn something to your Pioneer Drive, instead doing a full blown install.

---

### Post by sirzepp on 2008-01-24
Alright I gave those command line options a shot, here is the terminal output:

[INDENT]
sirzepp@sirzepp-desktop:~/Desktop$ sudo cdrecord dev=/dev/scd0 -dummy -v ubuntu-7.10-desktop-i386.iso
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-212D'
Revision       : '1.24'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   695 MB        
Total size:      799 MB (79:10.05) = 356254 sectors
Lout start:      799 MB (79:12/04) = 356254 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation

    Capacity  Blklen/Sparesz.  Type
           0             2048  Unformated or Blank Media
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 3592
Starting to write CD/DVD/BD at speed 40 in dummy SAO mode for single session.
Last chance to quit, starting dummy write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Sending CUE sheet...
cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
cdrecord: Input/output error. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 10 40 A8 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
Sense flags: Blk 100663328 (not valid) 
cmd finished after 0.019s timeout 200s
cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
cdrecord: Cannot send CUE sheet.
cdrecord: Could not write Lead-in.
Writing  time:    0.144s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
[/INDENT]

It still won't send the CUE sheet.  It is strange.  I can continue testing after I install an IDE DVD burner...because I'll still have my old SATA CD-R installed as my secondary Optical drive.  I'll see if I can't get to the bottom of this...and I'll keep this thread updated.  For now, as this is my ONLY issue with Ubuntu, I'll just get the IDE drive...that'll let me have full functionality while I also trouble shoot this on the old SATA burner.  My BIOS doesn't have the option to emulate PATA for the SATA controller...just for the IDE RAID controller:(.

---

### Post by sirzepp on 2008-01-24
I just realized that other wodim option we there...I'll give that a shot as well.

(goes to terminal)

Bummer, it gave me the same output/error as when I tried to write in -tao from K3b.

[INDENT]sirzepp@sirzepp-desktop:~/Desktop$ sudo wodim  dev=/dev/scd0 ubuntu-7.10-desktop-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-212D'
Revision       : '1.24'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 7056 KB/s
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 06 00 00 20 0E 24 08 10 40 A8 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA8 Qual 0x04 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
Sense flags: Blk 100663328 (not valid) 
cmd finished after 0.081s timeout 40s
write track data: error after 0 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.007s timeout 480s
cmd finished after 0.007s timeout 480s
wodim: Cannot fixate disk.
[/INDENT]

---

### Post by disturbed1 on 2008-01-24
Beyond my level here, but I'd check if your mappings are correct. Is cdrecord/wodim actually attempting to write to the correct device. This was a bug in udev for 32bit that was noted as being fixed, maybe it slipped through the 64bit fix?

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/23203](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/23203)

[http://forums.gentoo.org/viewtopic-t-645947.html](http://forums.gentoo.org/viewtopic-t-645947.html)

---

### Post by Mitchlb on 2008-01-24
I feel smothered with logs! lol. 

It is typically easiest to use one of the GUI programs to burn a data or audio CD. These are typically graphical front ends to the command line programs cdrecord. My favorite for ease of use and creating / copying CD's is X-CdRoast.I also really like Fire Burner. Also, it may be a dumb question and i don't mean to insult you, but are you using the right type of cd? What are u using?

---

### Post by Mitchlb on 2008-01-24
Also, try to burn something else. The file your trying to burn might be the problem. A broken .iso it looks like. Are you burning a version of ubuntu?

---

### Post by Mitchlb on 2008-01-24
I think "no preemp swab copy" is key. I'll look it up.

---

### Post by sirzepp on 2008-01-24
OK, I installed my new IDE DVD/CD Burner and it works flawlessly with all programs.  I've still got my old SATA burner installed...and I've tried a few different files(including a music CD).  So far, nothing.  What is "no preemp swab copy"?  Thanks for you help!

I'll keep working on it...it's nice to have a working burner and be able to work the problem without losing productivity!

---

### Post by sirzepp on 2008-01-24
I think it might be a mapping issue, but I have no idea how to fix it.  I read a post somewhere in my research(wish I would have saved it) about SATA burners not working when mapped to /dev/scd* and that an older release of Ubuntu switched them to /dev/hd*, in that post the user said when he upgraded to 7.04 SATA burning stopped working again...so he looked at the mapping and found it had been switched back to /dev/scd*.  He was getting the exact same errors I have(lots of things about CUE sheets, etc.).  Again, I'm also in way over my head, so I don't know what to do from here.  I'll keep tinkering.

---

### Post by disturbed1 on 2008-01-24
> **sirzepp said:**
> I think it might be a mapping issue, but I have no idea how to fix it.  I read a post somewhere in my research(wish I would have saved it) about SATA burners not working when mapped to /dev/scd* and that an older release of Ubuntu switched them to /dev/hd*, in that post the user said when he upgraded to 7.04 SATA burning stopped working again...so he looked at the mapping and found it had been switched back to /dev/scd*.  He was getting the exact same errors I have(lots of things about CUE sheets, etc.).  Again, I'm also in way over my head, so I don't know what to do from here.  I'll keep tinkering.

Look at the gentoo forum link I posted above about fixing the mapping issue, it's detailed in that ;)
> 
-nopreemp
              If this flag is present, all TOC entries for subsequent audio tracks will indicate that the audio data has been mastered with linear data - this is the default.

 -nocopy
              If  this flag is present, all TOC entries for subsequent audio tracks of the resulting CD will indicate that the audio data has permission to be copied only once for personal use
              - this is the default.

 -swab  If this flag is present, audio data is assumed to be in byte-swapped (little-endian) order.  Some types of CD-Writers e.g. Yamaha, Sony and  the  new  SCSI-3/mmc  drives  require
              audio  data to be presented in little-endian order, while other writers require audio data to be presented in the big-endian (network) byte order normally used by the SCSI proto&#8208;
              col.  Cdrecord knows if a CD-Recorder needs audio data in big- or little-endian order, and corrects the byte order of the data stream to match the needs  of  the  recorder.   You
              only need the -swab flag if your data stream is in Intel (little-endian) byte order.

              Note  that  the  verbose output of cdrecord will show you if swapping is necessary to make the byte order of the input data fit the required byte order of the recorder.  Cdrecord
              will not show you if the -swab flag was actually present for a track.

So by passing no preemp swab copy your just making sure cdrecord does what it's default settings are.

---

### Post by Zimmer on 2008-01-24
Not something silly like the jumper settings , is it?  What should it be, Master or slave? Looking at your outputs you seem to have another CD ROM device as hdb. If that is so you could try disconnecting the other and setting your DVD to master (I am unfamiliar with SATA so if the jumper setting is irrelavent for them please tell me :)  ) and try burning with just the new drive attached.

---

### Post by disturbed1 on 2008-01-24
> **Zimmer said:**
> Not something silly like the jumper settings , is it?  What should it be, Master or slave? Looking at your outputs you seem to have another CD ROM device as hdb. If that is so you could try disconnecting the other and setting your DVD to master (I am unfamiliar with SATA so if the jumper setting is irrelavent for them please tell me :)  ) and try burning with just the new drive attached.

SATA doesn't use jumpers, each device is *master* That's one of the advantages over PATA plus using a smaller cable instead of the bulky 80 pin IDE cable.

---

### Post by sirzepp on 2008-01-24
> **disturbed1 said:**
> Look at the gentoo forum link I posted above about fixing the mapping issue, it's detailed in that ;)
So by passing no preemp swab copy your just making sure cdrecord does what it's default settings are.

Oops...next time i'll read better.  I think I'm done tinkering for tonight...but I'll get back to this and play around with the mappings AND the cdrecord parameters.

---

### Post by Zimmer on 2008-01-24
> **disturbed1 said:**
> SATA doesn't use jumpers, each device is *master* That's one of the advantages over PATA plus using a smaller cable instead of the bulky 80 pin IDE cable.

Ah. Thanks.

All the same, it may still be worth disconnecting the other drive in case the cdrecord program is having a problem deciding which master to serve, even though they are on different controllers and cables...just a reckless thought. I apologise in advance if you have already tried this ... :)

---

### Post by Motorhead Kaze on 2008-01-27
I have been posting all week regarding this same problem and it appears to be coming from this cdrtools issue. 

Most of the comments in this thread are just a little over my head for now, as I don't know how to post logs (yet) but I can't burn with K3b because I Cdrecord has no permission to open my device.

I spent hours and hours on the forum, pasting in code into the terminal, trying to find what my computer's trip was, thinking it was hardware, then blaming K3b, now I'm on the trail of cdrecord.

Currently I can burn and view cdrs but cannot burn DVDs from .cue or .iso files.  I cannot copy DVDs (using K3b) either.

So if I missed something good in this post that wasn't noob proof I apologize.  Did you guys find a way to fix this cdrecord problem?

I'm on Gutsy using the latest K3b version.  So far, on the thread I started, I was asked for some info, this is what I got
My cdrecord -version
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling

groups
kaze adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev

dmesg | grep -i cd | grep -i rom   gets this:
[ 31.584642] hdc: DVD DC DW1670, ATAPI CD/DVD-ROM drive
[ 32.623641] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[ 32.623656] Uniform CD-ROM driver Revision: 3.20

 uname -a
Linux kaze 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

If I can help anyone help me figure this out, it would be wonderful.

My last K3b error was

"Using Wodim 1.1.6 - Copywrite (c) 2006 Cdrkit suite contributors
starting SAO writing speed at 48x
Cd record has no permission to open device"

---

