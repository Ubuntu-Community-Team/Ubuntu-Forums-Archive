---
title: "MacBook Pro 1,1 Ubuntu 9.04 Install Help"
date: 2009-07-23
forum: Apple Hardware Users
---

### Post by shep_fc3 on 2009-07-23
I have successfully run Hardy and Intrepid on my Macbook, but I tried to install Jaunty with no avail.  I think I've messed up my boot records, and can't get any linux variant to boot now.  I'm trying to dual boot OS X and Ubuntu 9.04 using the u-lite destop.  I wasn't able to use ext4 for my filesystem, so I've tried reinstalling multiple times.  During one of the installs, I accidentally installed grub into the MBR.  Refit show three tux icons "Boot Linux from Hard Drive", "Boot Linux from OSX", and "Boot Linux from Partition #3".  The last one is the correct option, but when I select it I just get the text GRUB with a flashing cursor.  I've reinstalled grub multiple times using root (hd0,2) and setup (hd0,2), but I still can't get it to boot.  

Here is my output from diskutil list:

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *93.2 Gi    disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS OSX                     89.9 Gi    disk0s2
   3:       Microsoft Basic Data UNTITLED                2.8 Gi     disk0s3
   4:                 Linux Swap                         308.2 Mi   disk0s4
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *111.8 Gi   disk1
   1:                 DOS_FAT_32 NO NAME                 50.0 Gi    disk1s1
   2:                      Linux UNTITLED                41.1 Gi    disk1s3
   3:                  Apple_HFS MacBackup               20.0 Gi    disk1s2
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *16.0 Mi    disk2
   1:        Apple_partition_map                         31.5 Ki    disk2s1
   2:                  Apple_HFS rEFIt                   16.0 Mi    disk2s2

Here is what rEFIt shows:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    188880887  Mac OS X HFS+
 3      188880888    194740263  Basic Data
 4      194740264    195371534  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    188880887  af  Mac OS X HFS+
 3      188880888    194740263  83  Linux
 4      194740264    195371534  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: GRUB
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 188880888:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 194740264:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

---

### Post by shep_fc3 on 2009-07-23
Well I was finally able to install Intrepid using the Guided partitioner and letting it install Grub wherever it wanted.  I then just used apt to do a dist-upgrade to Jaunty.  This also cleared up one of my Tux icons on rEFIt.  Here is what I did:

Downloaded Ubuntu 8.10 mini.iso
typed cli at the command line
ran through the normal install procedure
when it came to the partitioning, I deleted the / and the swap partitions I had created before
I then used the guided using largest continuous free space option.  
Everything after that went very smooth on the install.

Then I rebooted and updated my /etc/apt/sources.list to use the jaunty sources
apt-get update
apt-get dist-upgrade

Hope this is helpful for others.

---

