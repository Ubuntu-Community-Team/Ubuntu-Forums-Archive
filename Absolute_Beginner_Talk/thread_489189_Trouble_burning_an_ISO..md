---
title: "Trouble burning an ISO."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-01
Edit: I downloaded ImgBurn and it worked great. It is the only ISO burner that I could get to work with my faulty CDs.  I had used the CD/R-W disks and somehow messed every one up (10) using k3b. I had used k3b earlier with no problems. i tried other ISO burners but none worked. I finally came across the mention of ImgBurn.  ImgBurn burned the CDs as though nothing was wrong.

Can someone tell me from the following why I am having problems burning an ISO to a CD? Thanks for your help.
kh

[php]kittyhawk63

4C85-2031-3005-0001-0556-X2E0-0900-4025-1E23-9171*

Windows XP 5.1
IA32
WinAspi: -
ahead WinASPI: File 'C:\Program Files\Nero\Nero 7\Core\Wnaspi32.dll': Ver=2.0.1.74, size=164112 bytes, created 11/2/2004 1:54:32 PM 

NT-SPTI used
Nero Version: 7.2.3.2
Internal Version: 7, 2, 3, 2
 (Nero Express)
Recorder:             <LITE-ON DVDRW LH-20A1P>  Version: KL0G - HA 1 TA 1 - 7.2.3.2
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      2048kB
 Bus Type      :      via Inquiry data (1) -> ATAPI, detected: ?
 Connected to MMC as unknown drive with class-nr : 1
 Drive is autodetected - recorder class: Std. MMC recorder
CD-ROM:               <COMPAQ   CD-ROM LTN403   >Version: DQ24 - HA 1 TA 0 - 7.2.3.2
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
DiskPeripheral       : ST3160812A                       atapi Port 0 ID 0  DMA: On 
DiskPeripheral       : ST380013A                        atapi Port 0 ID 1  DMA: On 
CdRomPeripheral      : COMPAQ CD-ROM LTN403             atapi Port 1 ID 0  DMA: Off
CdRomPeripheral      : LITE-ON DVDRW LH-20A1P           atapi Port 1 ID 1  DMA: On 

=== CDRom-Device-Map ===
COMPAQ CD-ROM LTN403       E:   CDRom0
LITE-ON DVDRW LH-20A1P     F:   CDRom1
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 74448896 (0) Byte
BUFE           : 0
Physical memory     : 511MB (523824kB)
Free physical memory: 227MB (232504kB)
Memory in use       : 55 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

30.6.2007
CD Image
4:57:40 PM    #1 Text 0 File Burncd.cpp, Line 3086
    LITE-ON DVDRW LH-20A1P
    SMART-BURN activated
    
4:57:40 PM    #2 Text 0 File ThreadedTransfer.cpp, Line 531
    ReadBuffer-Pipe got 72704KB of Memory
    
4:57:40 PM    #3 Text 0 File Reader.cpp, Line 124
    Reader running
    
4:57:40 PM    #4 Text 0 File Writer.cpp, Line 113
    Writer F: LITE-ON DVDRW LH-20A1P running
    
4:57:41 PM    #5 Text 0 File Burncd.cpp, Line 3400
    Turn on Track-At-Once, using CD-R/RW media
    
4:57:41 PM    #6 Text 0 File DlgWaitCD.cpp, Line 289
    Last possible write address on media:   359848 ( 79:59.73)
    Last address to be written:             357259 ( 79:25.34)
    
4:57:41 PM    #7 Text 0 File DlgWaitCD.cpp, Line 301
    Write in overburning mode: NO (enabled: CD)
    
4:57:41 PM    #8 Text 0 File DlgWaitCD.cpp, Line 2715
    Recorder: LITE-ON DVDRW LH-20A1P
    
4:57:41 PM    #9 Text 0 File DlgWaitCD.cpp, Line 473
    >>> Protocol of DlgWaitCD activities: <<<
    =========================================
    
4:57:41 PM    #10 Text 0 File ThreadedTransferInterface.cpp, Line 847
    Setup items (after recorder preparation)
     0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
        2 indices, index0 (150) not provided
        original disc pos #0 + 357260 (357260) = #357260/79:23.35
        relocatable, disc pos for caching/writing not required/not required,  patch infos
        -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 357258 blocks [F: LITE-ON DVDRW LH-20A1P]
    --------------------------------------------------------------
    
4:57:41 PM    #11 Text 0 File ThreadedTransferInterface.cpp, Line 1059
    Prepare recorder [F: LITE-ON DVDRW LH-20A1P] for write in TAO
    DAO infos:
    ==========
     MCN: ""
     TOCType: 0x00; Session Closed, disc fixated
     Tracks 1 to 1:
       1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200     731975680, ISRC ""
    DAO layout:
    ===========
     __Start_|____Track_|_Idx_|_CtrlAdr_|_RecDep__________
        -150 |  lead-in |   0 |    0x41 | 0x00
        -150 |        1 |   0 |    0x41 | 0x00
           0 |        1 |   1 |    0x41 | 0x00
      357260 | lead-out |   1 |    0x41 | 0x00
    
4:57:41 PM    #12 Text 0 File ThreadedTransferInterface.cpp, Line 1127
    Removed 2 run-out blocks from end of track 1. Length: 357260 -> 357258.
    
4:57:41 PM    #13 Text 0 File SCSIPassThrough.cpp, Line 39
    SPTILockVolume - completed successfully for FCTL_LOCK_VOLUME
    
4:57:41 PM    #14 Text 0 File SCSIPassThrough.cpp, Line 84
    SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
    
4:57:41 PM    #15 Phase 24 File dlgbrnst.cpp, Line 1730
    Caching of files started
    
4:57:41 PM    #16 Text 0 File Burncd.cpp, Line 4231
    Cache writing successful.
    
4:57:41 PM    #17 Phase 25 File dlgbrnst.cpp, Line 1730
    Caching of files completed
    
4:57:41 PM    #18 Phase 28 File dlgbrnst.cpp, Line 1730
    Speed measurement started
    
4:57:41 PM    #19 Text 0 File ThreadedTransferInterface.cpp, Line 2707
    Verifying disc position of item 0 (relocatable, no disc pos, patch infos, orig at #0): write at #0
    
5:00:26 PM    #20 Text 0 File ThreadedTransfer.cpp, Line 228
    all writers idle, stopping conversion
    
5:00:26 PM    #21 Phase 29 File dlgbrnst.cpp, Line 1679
    Speed measurement completed: 34.2x (5,140 KB/s)
    
5:00:26 PM    #22 Phase 36 File dlgbrnst.cpp, Line 1730
    Burn process started at 4x (600 KB/s)
    
5:00:26 PM    #23 SPTI -1189 File SCSIPassThrough.cpp, Line 291
    F: CdRom1: SCSIStatus(x02) WinError(0) NeroError(-1189)
    Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
    Sense Code: 0x30
    Sense Qual: 0x02
    CDB Data:   0xAD 00 00 00 00 00 00 FF 40 00 00 00 
    Sense Area: 0x70 00 05 00 00 00 00 0A 00 00 00 00 30 02 
    Buffer x0369ca00: Len x4000
    
5:00:26 PM    #24 Text 0 File ThreadedTransferInterface.cpp, Line 2707
    Verifying disc position of item 0 (relocatable, no disc pos, patch infos, orig at #0): write at #0
    
5:00:26 PM    #25 Text 0 File MMC.cpp, Line 22035
    Set BUFE: SMART-BURN -> ON , SMART-BURN : ON
    
5:01:46 PM    #26 SPTI -1106 File SCSIPassThrough.cpp, Line 291
    F: CdRom1: SCSIStatus(x02) WinError(0) NeroError(-1106)
    Sense Key:  0x03 (KEY_MEDIUM_ERROR)
    Sense Code: 0x73
    Sense Qual: 0x03
    CDB Data:   0x2A 00 00 00 00 00 00 00 20 00 00 00 
    Sense Area: 0x70 00 03 00 00 00 00 0A 00 00 00 00 73 03 
    Buffer x049b0000: Len x10000
    0x00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    0x00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    0x00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    
5:01:46 PM    #27 CDR -1106 File Writer.cpp, Line 302
    Power calibration error
    F: LITE-ON DVDRW LH-20A1P
    
5:01:46 PM    #28 Text 0 File ThreadedTransfer.cpp, Line 228
    all writers idle, stopping conversion
    
5:01:46 PM    #29 Text 0 File ThreadedTransfer.cpp, Line 222
    conversion idle, stopping reader
    
5:01:47 PM    #30 CDR -201 File WriterStatus.cpp, Line 200
    Invalid write state
    F: LITE-ON DVDRW LH-20A1P
    
5:01:47 PM    #31 TRANSFER -18 File WriterStatus.cpp, Line 200
    Could not perform EndTrack
    
5:01:47 PM    #32 Text 0 File MMC.cpp, Line 16846
    <LITE-ON DVDRW LH-20A1P  > start Close Session
    
5:01:47 PM    #33 Phase 38 File dlgbrnst.cpp, Line 1730
    Burn process failed at 4x (600 KB/s)
    

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 0 (Security Option)[/php]

---

### Post by hackarre on 2007-07-01
Are you talking from windows? If you have this problem with windows I would leave it and I would download some programs like alcohol 120.

I would also try reinstalling and changing the speed of burning.

---

### Post by Raineer on 2007-07-01
On my Windows PC's I use [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").  Works pretty well and is very lean. In Linux it's typically Gnomebaker, though Nero for Linux V3 is pretty nice as well...if I really need to verify the data carefully I'll use Nero.

---

### Post by chemtut on 2007-07-01
find imgburn    with google
download---it is free
burn at 1* speed---it has never failed me

---

### Post by abn91c on 2007-07-01
from windows download Active ISO Burner 1.1 from [www.download.com](www.download.com), it is free it can burn CDR and DVD ISO's with just 2 clicks. You can burn all the way to 32x. I never had a disk fail even when recording at 32x. Yhat is how i got all my live cd's :D

---

### Post by steveneddy on 2007-07-01
Nero is capable of burning an .iso file to CD, you just have to tell it that you want to burn an .iso, not a data file.

---

### Post by jKat~ on 2007-07-18
ImgBurn worked perfectly! I’ve made many coasters with Nero 6 choosing every possible option for burning bootable ISO images. ImgBurn worked on my first try. And I didn’t have to change any settings! Thanks.

What am I using?
Sony VAIO PCG-f560
PIII/600
192MB/9GB

---

