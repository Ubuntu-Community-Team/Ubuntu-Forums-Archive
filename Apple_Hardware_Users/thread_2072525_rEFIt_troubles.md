---
title: "rEFIt troubles"
date: 2012-10-18
forum: Apple Hardware Users
---

### Post by EMEEAE on 2012-10-18
I recently downloaded and installed rEFIt and Ubuntu 12.04 on my macbook pro 6,2.  I did this in the following order:

1. installed refit, rebooted to affirm it boots to refit.
2. downloaded Ubuntu (verified md5) and burned iso to DVD.
3. partitioned 60 GB of free space in disk utility
4. inserted DVD, rebooted, from refit boot screen booted to Ubuntu install DVD.
5. Selected "try Ubuntu", booted to ubunto, used gparted to create 4 GB of "swap" from unallocated space and the rest (~56GB) "ext4". apply changes
6. Started Install from desktop shortcut. 
7. when asked to "dual boot", "overwrite", "my own thing",  I selected my own thing.  Selected the ext4 partition (56 GB) as the location of the install and location of the bootloader install. Set the mount point of the partiton as "/". Clicked "install now". It finished installing, i rebooted and once at the refit screen I went the the refit partition tool and fixed my partition tables that no longer matched.

Here's where it falls apart.  When I boot to linux from refit it goes to a grayed out picture of the linux penguin...forever. Are my partition maps still wrong? Do I need to create a hybrid MBR? (google)  Anyway, partition inspector gives me the following:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA         End LBA        Type
 1             40           409639         EFI System (FAT)
 2         409640       855138647  Mac OS X HFS+
 3      855138648    856408183  Mac OS X Boot
 4      856410112    864602111  Linux Swap
 5      864602112    976773119  Basic Data

Current MBR partition table:
 # A    Start LBA       End LBA        Type
 1              1            409639         ee  EFI Protective
 2 *       409640      855138647   af  Mac OS X HFS+
 3      855138648    856408183  ab  Mac OS X Boot
 4      856410112    864602111  82  Linux swap / Solaris

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 855138648:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 856410112:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 864602112:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data

---

