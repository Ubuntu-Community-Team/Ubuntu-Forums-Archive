---
title: "Windows is unable to detect NTFS partion created by GParted"
date: 2011-12-15
forum: Apple Hardware Users
---

### Post by libin_v on 2011-12-15
Hi All,

Both Mac OS & Ubuntu is able to read/write into the NTFS partition created by GParted however, windows is unable to detect it. Please advise as to how I can solve this.

Below I have pasted the output of gptsync & gdisk. Also I have attached is the screenshot of GParted. BTW I am using Macbook Pro 6,1

$ sudo gptsync /dev/sda
```

Current GPT partition table:
#      Start LBA      End LBA  Type
1             40       409639  EFI System (FAT)
2         409640    463880231  Mac OS X HFS+
3      464144384    589144383  Basic Data
4      589144384    714144384  Basic Data
5      714144385    745394385  Linux Swap
6      745396224    976773119  EFI System (FAT)

Current MBR partition table:
# A    Start LBA      End LBA  Type
1              1           39  ee  EFI Protective
2             40       409639  0b  FAT32 (CHS)
3         409640    463880231  af  Mac OS X HFS+
4 *    464144384    589144383  07  NTFS/HPFS

Status: Analysis inconclusive, will not touch this disk.

```$ sudo gdisk -l /dev/sda
```

GPT fdisk (gdisk) version 0.6.14

Partition table scan:
 MBR: hybrid
 BSD: not present
 APM: not present
 GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 43422C81-9B64-4A2F-8F32-BA30510EF88E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 266011 sectors (129.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
  1              40          409639   200.0 MiB   EF00  EFI System Partition
  2          409640       463880231   221.0 GiB   AF00  Mac
  3       464144384       589144383   59.6 GiB    0700  BOOTCAMP
  4       589144384       714144384   59.6 GiB    0700
  5       714144385       745394385   14.9 GiB    8200
  6       745396224       976773119   110.3 GiB   0700

```--
Libin

---

