---
title: "Troubleshooting Ubuntu 11.10 installation with Mac OS 10.7 on MacBookPro 7.1"
date: 2011-12-02
forum: Apple Hardware Users
---

### Post by cyberdude77 on 2011-12-02
MacBookPro 7.1
MacOs 10.7.2

Attempting to install Ubuntu 11.10

I followed the instructions on the following website. [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

When I try to sync the partition tables with rEFIT, I get the following error message.

[/INDENT]Status: Analysis inconclusive, will not touch this disk.
[/INDENT]Error: Not found returned from gptsync.efi

If I try to boot by clicking on the Linux logo, the boot stalls on a grey screen.

Here is the report from the Partition Inspector

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    391034639  Mac OS X HFS+
 3      391034640    392304175  Mac OS X Boot
 4      392304640    486348799  Basic Data
 5      486348800    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  0b  FAT32 (CHS)
 3 *       409640    391034639  af  Mac OS X HFS+
 4      391034640    392304175  af  Mac OS X HFS+

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)
 Listed in MBR as partition 2, type 0b  FAT32 (CHS)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+, active

Partition at LBA 391034640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 392304640:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data

Partition at LBA 486348800:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Any help would be greatly appreciated.

---

