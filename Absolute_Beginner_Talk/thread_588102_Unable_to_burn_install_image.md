---
title: "Unable to burn install image"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by d00by on 2007-10-23
I am unable to make a CD for ubuntu 7.10 gutsy.

I checked the md5 sum hash of the x386 ISO. It matched with the official ISO d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso

is it a burning issue or corrupt CD issue? I have tried burning on 2 CD RWs and 1 CD R.

I have the following laptop config

```
Operating System 	  	System Model
Windows XP Professional Service Pack 2 (build 2600) 	  	Hewlett-Packard Presario V3000 (RZ819PA#ACJ) F.23

Enclosure Type: Notebook
Processor a 	  	Main Circuit Board b
2.00 gigahertz AMD Turion 64
16 kilobyte primary memory cache
512 kilobyte secondary memory cache 	  	Board: Wistron 30B5 62.54
Bus Clock: 200 megahertz
BIOS: Hewlett-Packard F.23 02/13/2007
Drives 	  	Memory Modules c,d
80.02 Gigabytes Usable Hard Drive Capacity
11.79 Gigabytes Hard Drive Free Space

MATSHITA DVD-RAM UJ-850S [CD-ROM drive]

ST980811AS [Hard drive] (80.03 GB) -- drive 0, s/n 5LY2SY2Y, rev 3.BHD, SMART Status: Healthy 	  	992 Megabytes Installed Memory

Slot 'M1' has 512 MB
Slot 'M2' has 512 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	44.51 GB 	5.27 GB free
e: (NTFS on drive 0) 	35.52 GB 	6.51 GB free
```

I am getting this error during burning on CD RW disc.

```
Windows XP 5.1
IA32
WinAspi: -

NT-SPTI used
Nero Version: 7.8.5.0
Internal Version: 7, 8, 5, 0

Recorder:             <MATSHITA DVD-RAM UJ-850S>Version: 1.05 - HA 1 TA 0 - 7.8.5.0
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
CD-ROM:               <MATSHITA DVD-RAM UJ-850S >Version: 1.05 - HA 1 TA 0 - 7.8.5.0
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
CdRomPeripheral      : MATSHITA DVD-RAM UJ-850S         atapi Port 1 ID 0  DMA: On 
DiskPeripheral       : ST980811AS                       nvata Port 2 ID 0  DMA: Off

=== CDRom-Device-Map ===
MATSHITA DVD-RAM UJ-850S   D:   CDRom0
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 990MB (1014376kB)
Free physical memory: 422MB (432980kB)
Memory in use       : 57 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

23.10.2007
CD Image
18:26:58	#1 Text 0 File SCSIPTICommands.cpp, Line 411
	LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	
18:26:58	#2 Text 0 File Burncd.cpp, Line 3187
	MATSHITA DVD-RAM UJ-850S
	Buffer underrun protection activated
	
18:26:58	#3 Text 0 File Burncd.cpp, Line 3499
	Turn on Disc-At-Once, using CD-R/RW media
	
18:27:52	#4 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:   359848 ( 79:59.73)
	Last address to be written:             356253 ( 79:12.03)
	
18:27:52	#5 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO (enabled: CD)
	
18:27:52	#6 Text 0 File DlgWaitCD.cpp, Line 2949
	Recorder: MATSHITA DVD-RAM UJ-850S;
	   CDRW code: 00 97 32 10; OSJ entry from: Prodisc Technology Inc.
	   ATIP Data:
	     Special    Info [hex] 1: B3 00 CE, 2: 61 20 0A (LI 97:32.10), 3: 4F 3B 4A (LO 79:59.74)
	     Additional Info [hex] 1: 24 1A D8, 2: 26 B2 4A, 3: 00 00 00 (invalid)
	
18:27:52	#7 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	Compilation cannot be written on that medium type.
		(Medium in drive: CD-ROM. Medium required by compilation: CD-R/RW.)
	
18:27:52	#8 Text 0 File ThreadedTransferInterface.cpp, Line 793
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 356254 (356254) = #356254/79:10.4
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 356254 blocks [D: MATSHITA DVD-RAM UJ-850S]
	--------------------------------------------------------------
	
18:27:52	#9 Text 0 File Burncd.cpp, Line 4097
	Can only write at 1,500 KB/s instead of 3,600 KB/s to current disc.
	
18:27:52	#10 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [D: MATSHITA DVD-RAM UJ-850S] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200     729915392, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |   356254 |   356254 | 0x00
	   356254 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
18:27:52	#11 Text 0 File SCSIPTICommands.cpp, Line 209
	SPTILockVolume - completed successfully for FCTL_LOCK_VOLUME
	
18:27:52	#12 Text 0 File Burncd.cpp, Line 4278
	Caching options: cache CDRom or Network-Yes, small files-No (<64KB)
	
18:27:52	#13 Phase 24 File dlgbrnst.cpp, Line 1762
	Caching of files started
	
18:27:52	#14 Text 0 File Burncd.cpp, Line 4397
	Cache writing successful.
	
18:27:52	#15 Phase 25 File dlgbrnst.cpp, Line 1762
	Caching of files completed
	
18:27:52	#16 Phase 28 File dlgbrnst.cpp, Line 1762
	Speed measurement started
	
18:27:52	#17 Text 0 File ThreadedTransferInterface.cpp, Line 2721
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
18:27:52	#18 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 590400
	
18:28:10	#19 Text 0 File WriterStatus.cpp, Line 113
	<D: MATSHITA DVD-RAM UJ-850S> start writing Lead-Out at LBA 356254 (56F9Eh), length 0 blocks
	
18:28:10	#20 Phase 29 File dlgbrnst.cpp, Line 1711
	Speed measurement completed: 255.7x (38,368 KB/s)
	
18:28:11	#21 Phase 36 File dlgbrnst.cpp, Line 1762
	Burn process started at 10x (1,500 KB/s)
	
18:28:11	#22 Text 0 File ThreadedTransferInterface.cpp, Line 2721
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
18:28:11	#23 Text 0 File MMC.cpp, Line 17654
	StartDAO : CD-Text - Off
	
18:28:11	#24 Text 0 File MMC.cpp, Line 22344
	Set BUFE: Buffer underrun protection -> ON 
	
18:28:11	#25 Text 0 File MMC.cpp, Line 17882
	CueData, Len=32
	41 00 00 14 00 00 00 00 
	41 01 00 10 00 00 00 00 
	41 01 01 10 00 00 02 00 
	41 aa 01 14 00 4f 0c 04 
	
18:28:11	#26 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
18:28:12	#27 Text 0 File Cdrdrv.cpp, Line 1338
	18:28:12.062 - D: MATSHITA DVD-RAM UJ-850S : Queue again later
	
18:34:22	#28 SPTI -1040 File SCSIPassThrough.cpp, Line 179
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1040)
	Sense Key:  0x03 (KEY_MEDIUM_ERROR)
	Sense Code: 0x10
	Sense Qual: 0x00
	CDB Data:   0x2A 00 00 03 E9 40 00 00 20 00 00 00 
	Sense Area: 0xF1 00 03 00 03 E6 F4 0A 00 13 00 00 10 
	Buffer x088755c0: Len x10000
	0xC9 7C 45 C8 FA 1E F8 0A 6E 87 47 47 2B A2 19 B1 
	0xA3 36 14 BF 00 8C D5 47 CC 73 2E DC 93 90 B2 D9 
	0x45 C4 64 B3 D1 80 2F DD 95 83 36 23 74 79 59 D4 
	
18:34:22	#29 CDR -1040 File Writer.cpp, Line 303
	Illegal block size for command
	D: MATSHITA DVD-RAM UJ-850S
	
18:34:22	#30 Phase 38 File dlgbrnst.cpp, Line 1762
	Burn process failed at 10x (1,500 KB/s)
	
18:34:23	#31 Text 0 File SCSIPTICommands.cpp, Line 254
	SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
	
18:34:26	#32 Text 0 File Cdrdrv.cpp, Line 11214
	DriveLocker: UnLockVolume completed
	
18:34:26	#33 Text 0 File SCSIPTICommands.cpp, Line 411
	UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 0 (Security Option) 
```

---

### Post by Jorn.jambers on 2007-10-23
If the MD5 checksum matches i think its a burning problem. I suggest you try another burning tool. Like deepburner or so it's freeware.

kind regards

---

### Post by orange2k on 2007-10-23
Somewhere in your post I can see that your CD-recorder reports that no recordable media is present.
You may have a hardware problem with your CD-burner...

---

### Post by cfaulkner on 2007-10-23
Use the Nero Trial: [http://www.nero.com/enu/downloads-nero8-trial.php](http://www.nero.com/enu/downloads-nero8-trial.php)

---

### Post by d00by on 2007-10-23
> **orange2k said:**
> Somewhere in your post I can see that your CD-recorder reports that no recordable media is present.
You may have a hardware problem with your CD-burner...

That was due to a non-blank CD I had inserted. I inserted a CD-RW Disc after being prompted to add a blan k disk.

I have tried an alternate burner program PowerISO with no success. It failed at 60-70%.

if it is a hardware CD burner issue, I guess am s@re#ed! :(

---

### Post by Perpetual on 2007-10-23
Just curious, has your burner worked in the past?

Otherwise, your could buy or request the cd from Ubuntu ([http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)).  Or, maybe find someone in your part of the world who can send you a disc?  Are you running Ubuntu now?  Have you considered upgrading rather than a fresh install (assuming this is for your computer).

---

### Post by d00by on 2007-10-23
> **Perpetual said:**
> Just curious, has your burner worked in the past?

Otherwise, your could buy or request the cd from Ubuntu ([http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)).  Or, maybe find someone in your part of the world who can send you a disc?  Are your running Ubuntu now?  Have you considered upgrading rather than a fresh install (assuming this is for your computer).

It is a fairly new laptop. Thoug it is a cheap entry level one. :D

Yes, the burner works. I burn data on it frequently. Though most of it is media files.

I have ordered through shipit but it will take a month to reach me.

I am running XP SP2 on my laptop.

---

### Post by Perpetual on 2007-10-23
You could try a different burning program, ImageBurn which runs on Windows.  I used it exclusively back in my Windows days.  I have never had problems using it.  [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by d00by on 2007-10-23
> **Perpetual said:**
> You could try a different burning program, ImageBurn which runs on Windows.  I used it exclusively back in my Windows days.  I have never had problems using it.  [http://www.imgburn.com/](http://www.imgburn.com/)

It may be a h/w issue or maybe the CD is corrupted. Here is the fail log of image burn. The burn fails at 73%.

```
I 20:49:15 ImgBurn Version 2.3.2.0 started!
I 20:49:15 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 2)
I 20:49:15 Total Physical Memory: 1,014,376 KB  -  Available: 454,660 KB
I 20:49:15 Initialising SPTI...
I 20:49:15 Searching for SCSI / ATAPI devices...
I 20:49:15 Found 1 DVD±RW/RAM!
I 20:50:47 Operation Started!
I 20:50:47 Device: [1:0:0] MATSHITA DVD-RAM UJ-850S 1.05 (D:) (ATA)
I 20:50:47 Media Type: CD-RW (Disc ID: 97m32s10f) (Speeds: 4x, 8x, 10x)
I 20:50:47 Quick Erase: Yes
I 20:50:47 Erasing Disc...
I 20:51:19 Operation Successfully Completed! - Duration: 00:00:31
I 20:51:20 Operation Started!
I 20:51:20 Source File: E:\Users\Public\Downloads\misc\ubuntu-7.10-desktop-i386.iso
I 20:51:20 Source File Sectors: 356,254 (MODE1/2048)
I 20:51:20 Source File Size: 729,608,192 bytes
I 20:51:20 Source File Volume Identifier: Ubuntu 7.10 i386
I 20:51:20 Source File Application Identifier: MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING
I 20:51:20 Source File File System(s): ISO9660 (Bootable), Joliet
I 20:51:20 Destination Device: [1:0:0] MATSHITA DVD-RAM UJ-850S 1.05 (D:) (ATA)
I 20:51:20 Destination Media Type: CD-RW (Disc ID: 97m32s10f) (Speeds: 4x, 8x, 10x)
I 20:51:20 Destination Media Sectors: 359,847
I 20:51:20 Write Mode: CD
I 20:51:20 Write Type: SAO
I 20:51:20 Write Speed: MAX
I 20:51:20 Test Mode: No
I 20:51:20 BURN-Proof: Enabled
I 20:51:20 Filling Buffer... (40 MB)
I 20:51:22 Writing LeadIn...
I 20:51:38 Writing Image... (LBA: 0 - 356253)
W 20:57:28 Failed to Write Sectors 260864 - 260895 - ID CRC or ECC Error
W 20:57:28 Retrying (1 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (2 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (3 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (4 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (5 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (6 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (7 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (8 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (9 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (10 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (11 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (12 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (13 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (14 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (15 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (16 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (17 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (18 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (19 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:28 Retrying (20 of 20)...
W 20:57:28 Retry Failed - Cannot Write Medium - Incompatible Format
W 20:57:57 Retrying (21)...
W 20:57:57 Retry Failed - Cannot Write Medium - Incompatible Format
E 20:59:13 Failed to Write Sectors 260864 - 260895 - ID CRC or ECC Error
I 20:59:13 Synchronising Cache...
E 20:59:14 Failed to Write Image!
E 20:59:14 Operation Failed! - Duration: 00:07:54
I 20:59:14 Average Write Rate: 1,149 KB/s (7.7x) - Maximum Write Rate: 1,512 KB/s (10.1x)
```

---

### Post by Perpetual on 2007-10-23
Did some Googling and a glance through the ImgBurn forums and found that this error usually arises with bad media.  I have seen spindles that have a batch of bad discs in them.  Do you see any physical blemishes on the cd at all?

[http://www.google.com/search?q=IMGBURN+Retry+Failed+-+Cannot+Write+Medium+-+Incompatible+Format&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=IMGBURN+Retry+Failed+-+Cannot+Write+Medium+-+Incompatible+Format&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by d00by on 2007-10-23
I'll try burning on another disc and let you know

can i burn this iso on dvd?

---

### Post by Perpetual on 2007-10-23
Yeah.  You can burn it on a DVD.  ImgBurn supports both or use a different program.

---

### Post by d00by on 2007-10-23
Operation Successful! Yay!!! :)

Apparently I can burn on DVD but not on CD. My burner hates CDs apparently. Why did not I try burning on DVD before?? Go figure... :D


I will try installing it now. Wish me luck, Hopefully the burn was successfull.

---

### Post by d00by on 2007-10-23
I guess I spoke too soon.the install seems to be stuck. The orange bar is not moving. I am typing this from my phone. I verified the DVD burn usimg the imgburn app and it was successful. I guess I will try to check the DVD for defects using live cd option. :(

---

### Post by Perpetual on 2007-10-23
Argh.  Get beyond one problem, hit another.  What part of the install is it failing at?  Patitioning?  Copying?  Installing?  This has been a problem for others.  As another option, since you are having so much fun burning discs, you could try using the Alternate CD.  I hear it works sometimes when the Live CD fails.

---

### Post by d00by on 2007-10-23
> **Perpetual said:**
> Argh.  Get beyond one problem, hit another.  What part of the install is it failing at?  Patitioning?  Copying?  Installing?  This has been a problem for others.  As another option, since you are having so much fun burning discs, you could try using the Alternate CD.  I hear it works sometimes when the Live CD fails.

It seems to have froze as I type this. I chose start/install u untuat the menu option screen. After afew seconds the orange bar stopped moving and just froze.

So I rebooted and selected check cd for defects on the menu option. As I type this the orange progress bar seems to be stuck at the very last. At the bottom left of the orangeprogressbar a message is saying checking integrity yada yada yada. It seems stuck to me

There is  no god. Alternate cd? Naah! I am sick of this. I'm giving up 
man! Ubuntu hates my compaq laptop! :(

---

### Post by Perpetual on 2007-10-23
Ah, don't give up!

---

### Post by d00by on 2007-11-04
I was finally able to install after downloading and installing the alternate amd 64 version.

Apparently my laptop only likes the 64 bit version.

go figure! :)

All's well that ends well........

---

### Post by Perpetual on 2007-11-05
At least you didn't give up!

---

### Post by d00by on 2007-11-05
Trust Ubuntu to keep messing with me.

Now it is giving me sleepless nights with no audio.

[http://ubuntuforums.org/showthread.php?t=603202](http://ubuntuforums.org/showthread.php?t=603202)

The Ubuntu GOD hates me. He really hates me. He is giving me ubuntu hell. :D

---

### Post by Perpetual on 2007-11-05
Actually, the quiet hum of the fan ought to help you sleep even sounder.  

(I'm not a sound troubleshooter, sorry can't help you there...)

---

