---
title: "always have problems burning (ubuntu iso) onto cd-r disc"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-04-21
Hello,
I'm writing this message on a WinXp computer with an internal  HP CD-Writer+ 8100 series burner.I've downloaded the ubuntu 7.04 iso and have checked the md5sum, and the hashes match. So I have a perfect ISO downloaded. 

I've tried to burn the 
I've tried to create a CD from the newly downloaded file.

I've used Infra Recorder (the program suggested in [https://help.ubuntu.com/community/BurningIsoHowto)](https://help.ubuntu.com/community/BurningIsoHowto)),
Nero Burninng Rom, magicIso, IsoRecorder ([http://isorecorder.alexfeinman.com/v2.htm)](http://isorecorder.alexfeinman.com/v2.htm)), and I have not been successful. I've gotten error messages from all the programs. For example, Nero Burning Rom gave the following Error Log:


> 
1C83-721K-10E5-477X-405C-373E-****

Windows XP 5.1
IA32
WinAspi: -

NT-SPTI used
Nero Version: 7.8.5.0
Internal Version: 7, 8, 5, 0

Recorder:             <HP CD-Writer+ 8100>      Version: 1.0g - HA 1 TA 0 - 7.8.5.0
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      1024kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
CD-ROM:               <HP       CD-Writer+ 8100 >Version: 1.0g - HA 1 TA 0 - 7.8.5.0
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
DiskPeripheral       : QUANTUM FIREBALL CX13.0A         atapi Port 0 ID 0  DMA: On 
CdRomPeripheral      : HP CD-Writer+ 8100               atapi Port 1 ID 0  DMA: Off

=== CDRom-Device-Map ===
HP CD-Writer+ 8100         D:   CDRom0
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 49283072 (0) Byte
BUFE           : 0
Physical memory     : 319MB (327136kB)
Free physical memory: 125MB (128672kB)
Memory in use       : 60 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

21.4.2007
CD Image
1:40:45 PM	#1 Text 0 File SCSIPTICommands.cpp, Line 411
	LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	
1:40:47 PM	#2 Text 0 File Burncd.cpp, Line 3499
	Turn on Track-At-Once, using CD-R/RW media
	
1:40:48 PM	#3 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:   359848 ( 79:59.73)
	Last address to be written:             357993 ( 79:35.18)
	
1:40:48 PM	#4 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO (enabled: CD)
	
1:40:48 PM	#5 Text 0 File DlgWaitCD.cpp, Line 2949
	Recorder: HP CD-Writer+ 8100;
	   CDR code: 00 97 24 16; OSJ entry from: SONY Corporation
	   ATIP Data: ?
	
1:40:48 PM	#6 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
1:40:48 PM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 793
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 357994 (357994) = #357994/79:33.19
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 357992 blocks [D: HP CD-Writer+ 8100]
	--------------------------------------------------------------
	
1:40:50 PM	#8 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [D: HP CD-Writer+ 8100] for write in TAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200     733478912, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |   357994 |   357994 | 0x00
	   357994 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
1:40:50 PM	#9 Text 0 File ThreadedTransferInterface.cpp, Line 1066
	Removed 2 run-out blocks from end of track 1. Length: 357994 -> 357992.
	
1:40:50 PM	#10 Text 0 File SCSIPTICommands.cpp, Line 209
	SPTILockVolume - completed successfully for FCTL_LOCK_VOLUME
	
1:40:50 PM	#11 Text 0 File Burncd.cpp, Line 4278
	Caching options: cache CDRom or Network-Yes, small files-No (<64KB)
	
1:40:50 PM	#12 Phase 24 File dlgbrnst.cpp, Line 1762
	Caching of files started
	
1:40:51 PM	#13 Text 0 File Burncd.cpp, Line 4397
	Cache writing successful.
	
1:40:51 PM	#14 Phase 25 File dlgbrnst.cpp, Line 1762
	Caching of files completed
	
1:40:51 PM	#15 Phase 36 File dlgbrnst.cpp, Line 1762
	Burn process started at 4x (600 KB/s)
	
1:40:51 PM	#16 Text 0 File ThreadedTransferInterface.cpp, Line 2721
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
1:40:52 PM	#17 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 49265600
	
2:00:55 PM	#18 Text 0 File MMC.cpp, Line 17098
	<&#20552;&#8224;&#8224;&#8224;&#17152;&#11588;&#29271;&#29801;&#17475;&#22317;&#26994;&#25972;&#11122;&#14368;&#12337;&#8240;&#12544;&#12334;g&#305;> start Close Session
	
2:00:55 PM	#19 SPTI -1047 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x64
	Sense Qual: 0x00
	CDB Data:   0x51 00 00 00 00 00 00 00 20 00 00 00 
	Sense Area: 0x70 00 05 00 00 00 00 12 00 00 00 00 64 
	Buffer x060402c0: Len x20
	
2:00:55 PM	#20 CDR -1047 File ThreadedTransferInterface.cpp, Line 1242
	Illegal mode for this track
	D: HP CD-Writer+ 8100
	
2:00:56 PM	#21 Phase 38 File dlgbrnst.cpp, Line 1762
	Burn process failed at 4x (600 KB/s)
	
2:00:56 PM	#22 SPTI -1047 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x64
	Sense Qual: 0x00
	CDB Data:   0x1E 00 00 00 00 00 00 00 00 00 00 00 
	Sense Area: 0x70 00 05 00 00 00 00 12 00 00 00 00 64 
	
2:00:56 PM	#23 Text 0 File SCSIPTICommands.cpp, Line 254
	SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
	
2:00:56 PM	#24 SPTI -1047 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x64
	Sense Qual: 0x00
	CDB Data:   0x1B 00 00 00 02 00 00 00 00 00 00 00 
	Sense Area: 0x70 00 05 00 00 00 00 12 00 00 00 00 64 
	
2:00:56 PM	#25 SPTI -1047 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x64
	Sense Qual: 0x00
	CDB Data:   0x1E 00 00 00 00 00 00 00 00 00 00 00 
	Sense Area: 0x70 00 05 00 00 00 00 12 00 00 00 00 64 
	
2:00:56 PM	#26 SPTI -1047 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x64
	Sense Qual: 0x00
	CDB Data:   0x1B 00 00 00 02 00 00 00 00 00 00 00 
	Sense Area: 0x70 00 05 00 00 00 00 12 00 00 00 00 64 
	
2:00:56 PM	#27 Text 0 File Cdrdrv.cpp, Line 11214
	DriveLocker: UnLockVolume completed
	
2:00:56 PM	#28 Text 0 File SCSIPTICommands.cpp, Line 411
	UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 0 (Security Option) 

I was wondering whether the problem was with the CD drive that I have. Is there a way to check out the CD drive? Or can you tell me what is wrong?
Thanks!

---

### Post by alexlex on 2007-04-21
it sounds you have bad media.

I burn my iso on a blank dvd "up to 16x" but it only writes at 2.5 and i had all sorts of problems so i went and but a pack of good quality 8x dvds and i was successful.

---

### Post by hanzj on 2007-04-21
Alexlex, Thanks for your  reply. I do not know if it's because I have bad media. I do not know whether the problem is with the discs that I have or with the CD burning drive that I have, or with something else. I do not know how you are able to conclude that the problem is with my CD-R discs.

By the way, my HP CD-Writer+ 8100 can burn at a maximum of 4X speed.

And I'm using Sony Cd-R 700mb discs, which have been used before with success.

---

### Post by bobplano on 2007-04-21
try a different brand of cd's and if that doesn't work then you can blame it on your cd burning drive. it might have gotten dirty or something if it's been used for awhile

---

### Post by alexlex on 2007-04-21
> **hanzj said:**
> Alexlex, Thanks for your  reply. I do not know if it's because I have bad media. I do not know whether the problem is with the discs that I have or with the CD burning drive that I have, or with something else. I do not know how you are able to conclude that the problem is with my CD-R discs.

By the way, my HP CD-Writer+ 8100 can burn at a maximum of 4X speed.

And I'm using Sony Cd-R 700mb discs, which have been used before with success.

not a conclusion.. a conclusion would mean i had all the facts and ruled out all other possibilities...just an idea for you to try. It is what was wrong with mine and that is what i did and it worked. Sometimes cheap media can cause the worst problems.

good luck

---

### Post by alexlex on 2007-04-21
p.s. you should always have media that matches the write speed of you drive

---

