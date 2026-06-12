---
title: "Installing Windows XP after Ubuntu on Mac Mini"
date: 2012-09-25
forum: Apple Hardware Users
---

### Post by janod on 2012-09-25
Hello,

I followed this thread [http://ubuntuforums.org/showthread.php?t=1671331](http://ubuntuforums.org/showthread.php?t=1671331) and tried to install Windows XP on Mac Mini with MacOS and Ubuntu being already installed.

I created new Hybrid MBR and proceeded with an install of XP. When installation finished I rebooted the computer and tried to boot XP from hard disk via refit. I however got error message "Disk Error - No system found".

Any help appreciated.
Thanks.

Jan

p.s. here is my GPT and MBR setup, XP is installed on the last partition (no. 8 in GPT and no. 2 in MBR)

 ```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     31866919  Mac OS X HFS+
 3       31872960     32917184  Basic Data
 4       32917504     71979007  Basic Data
 5       71979008     91510257  Linux Swap
 6       91510258    130572757  Basic Data
 7      130572758    521197757  Basic Data
 8      521197758    625142414  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    521197757  ee  EFI Protective
 2 *    521197758    625142414  0c  FAT32 (LBA)
 3      625142415    625142447  0a  Unknown

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

Partition at LBA 31872960:
 Boot Code: GRUB
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 32917504:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data

Partition at LBA 71979008:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 91510258:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 6, type Basic Data

Partition at LBA 130572758:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 7, type Basic Data

Partition at LBA 521197758:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 8, type Basic Data
 Listed in MBR as partition 2, type 0c  FAT32 (LBA), active

Partition at LBA 625142415:
 Boot Code: None

```

---

### Post by janod on 2012-11-27
Hello,

I found that a partition where you plan to install XP must be at the end of hybrid MBR. I therefore moved XP partition to the end of my hybrid MBR but nevertheless I could not boot from it.

Then I found on some Microsoft web page that some installations of XP (especially OEM versions) simply won't boot on Mactel ... I therefore went for Win7 which works flawlessly.

Regards,
Jan

---

