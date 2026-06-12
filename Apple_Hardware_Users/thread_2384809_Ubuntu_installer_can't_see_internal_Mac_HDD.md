---
title: "Ubuntu installer can't see internal Mac HDD"
date: 2018-02-12
forum: Apple Hardware Users
---

### Post by banbourg on 2018-02-12
Hi folks, 

I've been trying to set up an Ubuntu 16.04 partition on my MacBook Pro (2017). I've created a dedicated 100gig partition for it (diskutil below). However when I try to install Ubuntu from my USB disk image, the installer can only detect the USB hard drive - it can't see the internal drive. Same problem arises if I try fdisk -l. Any help or advice would be much appreciated!

```
/dev/disk0 (internal):
#:                       TYPE NAME                    SIZE       IDENTIFIER
0:      GUID_partition_scheme                         251.0 GB   disk0
1:                        EFI EFI                     314.6 MB   disk0s1
2:                 Apple_APFS Container disk1         150.0 GB   disk0s2
3:       Microsoft Basic Data UbuntuPart              100.0 GB   disk0s3

/dev/disk1 (synthesized):
#:                       TYPE NAME                    SIZE       IDENTIFIER
0:      APFS Container Scheme -                      +150.0 GB   disk1
                              Physical Store disk0s2
1:                APFS Volume Macintosh HD            108.2 GB   disk1s1
2:                APFS Volume Preboot                 21.3 MB    disk1s2
3:                APFS Volume Recovery                509.8 MB   disk1s3
4:                APFS Volume VM                      1.1 GB     disk1s5

/dev/disk2 (external, physical):
#:                       TYPE NAME                    SIZE       IDENTIFIER
0:      GUID_partition_scheme                        *16.0 GB    disk2
1:                        EFI EFI                     209.7 MB   disk2s1
2:       Microsoft Basic Data UBUNTU                  15.8 GB    disk2s2


[X:~]$ diskutil info /dev/disk0s3
   Device Identifier:        disk0s3
   Device Node:              /dev/disk0s3
   Whole:                    No
   Part of Whole:            disk0

   Volume Name:              UbuntuPart
   Mounted:                  Yes
   Mount Point:              /Volumes/UbuntuPart

   Partition Type:           Microsoft Basic Data
   File System Personality:  ExFAT
   Type (Bundle):            exfat
   Name (User Visible):      ExFAT

   OS Can Be Installed:      No
   Media Type:               Generic
   Protocol:                 PCI-Express
   SMART Status:             Not Supported
   Volume UUID:              D571AF1C-6074-3F47-AF60-B2987240331B
   Disk / Partition UUID:    036C0F0D-3771-4562-A55F-67642719B407

   Disk Size:                100.0 GB (99998498816 Bytes) (exactly 195309568 512-Byte-Units)
   Device Block Size:        4096 Bytes

   Volume Total Space:       100.0 GB (99994304512 Bytes) (exactly 195301376 512-Byte-Units)
   Volume Used Space:        9.6 MB (9568256 Bytes) (exactly 18688 512-Byte-Units) (0.0%)
   Volume Available Space:   100.0 GB (99984736256 Bytes) (exactly 195282688 512-Byte-Units) (100.0%)
   Allocation Block Size:    131072 Bytes

   Read-Only Media:          No
   Read-Only Volume:         No

   Device Location:          Internal
   Removable Media:          Fixed

   Solid State:              Yes
```

---

### Post by ajgreeny on 2018-02-12
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

---

