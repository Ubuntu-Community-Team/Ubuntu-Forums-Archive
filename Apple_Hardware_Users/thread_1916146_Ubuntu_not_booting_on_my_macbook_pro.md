---
title: "Ubuntu not booting on my macbook pro"
date: 2012-01-27
forum: Apple Hardware Users
---

### Post by zatix on 2012-01-27
I just installed a dual boot in my macbook pro with mac osx and ubuntu, and the ubuntu OS is not booting.

I firstly installed mac osx in one partition, I created two others: one for a shared home dir and another one for the ubuntu OS. After it, I installed rEFIt and then ubuntu. I installed Grub in the same partition as ubuntu. rEFIT is detecting ubuntu but when I try to boot it the error "Missing Operating system" is thrown.

I booted a live cd and mounted the linux partition and run update-grub but I get the same error. I installed in the livecd gptsync but still same problem.

I don't know what else to do :(

I left here some info that can be useful:

```
$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS mac                     100.0 GB   disk0s2
   3:                  Apple_HFS home                    550.1 GB   disk0s3
   4:                 Linux Swap                         2.0 GB     disk0s4
   5:                        EFI                         97.7 GB    disk0s5

``` 

Partition Inspector output:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    195722143  Mac OS X HFS+
 3      195984288   1270398351  Mac OS X HFS+
 4     1270398352   1274304601  Linux Swap
 5     1274304602   1465149054  EFI System (FAT)

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    195722143  af  Mac OS X HFS+
 3      195984288   1270398351  af  Mac OS X HFS+
 4     1270398352   1274304601  82  Linux swap / Solaris

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

Partition at LBA 195984288:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 1270398352:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 1274304602:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 5, type EFI System (FAT)
```

Any ideas?

Thanks

---

### Post by scottstensland on 2012-03-05
I have exactly the same problem.  Did U get to a solution ?

---

