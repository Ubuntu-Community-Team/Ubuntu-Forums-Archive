---
title: "rEFIt does not see Ubuntu partition"
date: 2012-08-12
forum: Apple Hardware Users
---

### Post by chrisduds on 2012-08-12
When I get to the rEFIt menu it only shows Mac OS X. In the partition inspector it shows this:
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    725503591  Mac OS X HFS+
 3      725503592    726773127  Mac OS X Boot
 4      726773128    742773128  Linux Swap
 5      742773129    742777035  GRUB2 BIOS Boot
 6      742777036    976773118  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1             40       409639  ee  EFI Protective
 2         409640    725503591  af  Mac OS X HFS+
 3      725503592    726773127  af  Mac OS X HFS+
 4      726773128    742773128  82  Linux swap / Solaris

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)
 Listed in MBR as partition 1, type ee  EFI Protective

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 725503592:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 726773128:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 742773129:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type GRUB2 BIOS Boot

Partition at LBA 742777036:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 6, type Basic Data

It appears as though there is no MBR entry for the Ubuntu partition. Does this have something to do with it? Can I add the Ubuntu partition and then flag it as bootable with fdisk?

Edit: it appears as though the MBR supports only 4 primary partitions. Should I change the Linux swap partition in the MBR to the main Ubuntu partition and then flag it?

---

