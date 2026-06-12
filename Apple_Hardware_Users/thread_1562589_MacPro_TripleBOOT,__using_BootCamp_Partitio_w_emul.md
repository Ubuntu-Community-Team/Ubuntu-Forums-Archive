---
title: "MacPro TripleBOOT, ? using BootCamp Partitio w/ emulator"
date: 2010-08-27
forum: Apple Hardware Users
---

### Post by wbs75 on 2010-08-27
I have no Problems with reFit & automatic 64 Bit Kernal Boot command tweak in OSX terminal. With my triple/which is kindy a quad boot!!! MBR & Bootloader's are working great and very stable.   System is good until i Install Paralle Tools to Ubuntu Server.  Which you pretty much need to have install with out problems while in OSX.  i want to beable to boot natively via reFit UBuntu Partition and beable to run it via emulator bootcamp partition OSX.  Paralle Tools 5.0 with Windows 7 Pro Works as good as to be expected.  Im able to use Paralle w/ tools install.  I'm able to boot via refit to Windows Partition with no problems.  Paralle works ok with Ubuntu only if Paralle Tools install. Tools screws all kinds of settings up where i'm unable to boot to the bootcamp UBUNTU partition.  

Which emulator out there will work where i can run it under OSX 10.6.4 64 Bit Kernal and boot back via refit? 

Here my system & settings.  I just deleted UBUNTU Server Partition.  OSX DiskUtility when deleting with Paragon ExtFS converts it to EXT2.  I use EXT 4 when i install OS. 

MacPro4.1 , 8Core (16 Logical) , 2.3 GHz , 16 GB Ram OSX 10.6.4

1 EFI
2 OSX 10.6.5 XCode Dev Boot (35 GB Boot / Dev install Drive, Not main OS i use)
3 UBUNTU Server 
4 Linux Swap
5 Windows 7
6 Xcode 
7 MultiMedia
8 OSX 10.6.4 Main Drive
"note i leave 8 gigs of unused space at end of disk"
"reFit install on both OSX partitions"


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2       16082456     64891055  Mac OS X HFS+
 3       65155072    143259647  Basic Data
 4      159537152    276703231  Basic Data
 5      276703232    957392295  Mac OS X HFS+
 6      957654440    989685695  Mac OS X HFS+
 7      989947840   1235752975  Mac OS X HFS+
 8      143267670    159537151  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2       16082456     64891055  af  Mac OS X HFS+
 3 *     65155072    143259647  83  Linux
 4      159537152    276703231  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 16082456:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 65155072:
 Boot Code: None
 File System: ext2
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 159537152:
 Boot Code: Unknown, but bootable
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

Partition at LBA 276703232:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 5, type Mac OS X HFS+

Partition at LBA 957654440:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 6, type Mac OS X HFS+

Partition at LBA 989947840:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 7, type Mac OS X HFS+

Partition at LBA 143267670:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 8, type Linux Swap



If any body can help it would be very appreciative!!!    I need UBUNTU Server to beable to boot via reFit and run with OSX emulator.

Thanks

---

