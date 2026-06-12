---
title: "Windows 7 no longer boots after installing Ubuntu in Triple-Boot setup"
date: 2011-12-18
forum: Any Other OS
---

### Post by Cyrallath on 2011-12-18
I have a MacBook Pro with Mac OS X Version 10.6.8 and initially installed Windows 7 Ultimate x64 via BootCamp. This was working fine until I decided to also install Ubuntu 11.10 using rEFIt, loosely following [the instructions here]("https://help.ubuntu.com/community/MacBook/TripleBoot").

My disk partitions looked like this before:
```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            649.0 GB   disk0s2
   4:       Microsoft Basic Data BOOTCAMP                100.8 GB   disk0s3          

```I then split my OS X partition into two, to create the Ubuntu partition. After installing Ubuntu, my disk partition now looks like this:
```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            500.0 GB   disk0s2
   3:       Microsoft Basic Data                         148.9 GB   disk0s3
   4:       Microsoft Basic Data BOOTCAMP                100.8 GB   disk0s4

```Ubuntu works (with a few hiccups that I can fix later), but now Windows 7 no longer loads. I presume this is because its partition ID has changed from disk0s3 to disk0s4 and it no longer knows where to find the OS, but I don't know how to fix it. I've tried using Startup Repair thrice from the Windows 7 disk, but without any success (it doesn't seem to recognise any Operating Systems exist anyway).

This is what I get when attempting to boot Windows 7:
```

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings and then click "next."
3. Click 'repair your computer'.
 
If you do not have the disc, contact your system administrator or computer manufacturer for assistance.
File: \Boot\BCD
Status: 0xc0000225
Info: An error occured while attempting to read the boot configuration data.

```I tried following the instructions [here]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Windows+Bootloader+from+the+DVD") to recover the Windows Bootloader (Option Two), but I couldn't find a drive which contained \boot\BCD.

This is the output from the Partition Inspector which comes on the rEFIt disk image:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    976972135  Mac OS X HFS+
 3      977234280   1267988479  Basic Data
 4     1268250624   1465147391  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2 *           40       409639  0b  FAT32 (CHS)
 3         409640    976972135  af  Mac OS X HFS+
 4      977234280   1267988479  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: Windows BOOTMGR (Vista)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)
 Listed in MBR as partition 2, type 0b  FAT32 (CHS), active

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 977234280:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 1268250624:
 Boot Code: Windows BOOTMGR (Vista)

```I hope that's enough information; any help would be very much appreciated, thank you.

---

### Post by Cyrallath on 2011-12-25
As a follow-up, I was unable to solve the problem and ended up having to remove the Windows and Ubuntu partitions and start from scratch.

Don't use Mac OS X's Disk Utility GUI to remove partitions as it seemed to disappear the EFI partition from the GPT partition table; instead, prefer using diskutil from the Terminal.

---

