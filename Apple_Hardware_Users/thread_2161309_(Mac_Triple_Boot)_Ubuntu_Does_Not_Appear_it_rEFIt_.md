---
title: "(Mac Triple Boot) Ubuntu Does Not Appear it rEFIt after Windows isntallation"
date: 2013-07-10
forum: Apple Hardware Users
---

### Post by duaneadam on 2013-07-10
Everything was fine, I have both Mac OS and Ubuntu then after I finished installing Windows 7, Ubuntu disappeared from rEFIT list. However, partitions still exists.
It appears in GPT partition table but not MBR table. I think the solution is to fix MBR table but messing with the MBR table with little knowledge about it could lead to.. misleading results. I need help with the MBR table.

Below are the the generated report from Partition Inspector. The text in red is not in the report, I included it to explain which partition is which.
```


*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    500409639  Mac OS X HFS+
 3      500409640    501679175  Mac OS X Boot
 4      501680128    751677439  Basic Data [COLOR=#ff0000]<--- Windows 7 rests in here[/COLOR]
 5      751679488    972382207  Basic Data [COLOR=#ff0000]<--- Ubuntu rests in here[/COLOR]
 6      972384256    976773119  Linux Swap [COLOR=#ff0000]<--- This is partition for swap[/COLOR]


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    500409639  af  Mac OS X HFS+
 3      500409640    501679175  af  Mac OS X HFS+
 4 *    501680128    751677439  07  NTFS/HPFS


MBR contents:
 Boot Code: Unknown, but bootable


Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)


Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+


Partition at LBA 500409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type af  Mac OS X HFS+


Partition at LBA 501680128:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active


Partition at LBA 751679488:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Basic Data


Partition at LBA 972384256:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap



```

---

### Post by oldfred on 2013-07-10
Moved to Apple sub-forum
I do not know Macs.
But with a Mac and booting Windows you have to use the hybrid MBR/gpt partitioning. That can lead to many issues.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[URL="http://ubuntuforums.org/showthread.php?t=1908210"]http://ubuntuforums.org/showthread.php?t=1908210
[/URL]
 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

[URL="http://ubuntuforums.org/showthread.php?t=1908210"]
[/URL]

[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

