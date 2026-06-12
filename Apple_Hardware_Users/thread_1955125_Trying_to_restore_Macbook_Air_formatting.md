---
title: "Trying to restore Macbook Air formatting"
date: 2012-04-09
forum: Apple Hardware Users
---

### Post by tombaugh on 2012-04-09
Hi,

I'm trying to restore the partitioning of my late 2011 Air drive, after  messing it up while trying to dual boot OS X and Linux. At this point I'm a bit worried, so my first goal is to  get rid of the superfluous partitions and resize the OS X one so I can  use the whole drive again. I don't care about data loss. 

According to Disk Utility the partitioning looks like this:

EFI
Macintosh HD
Recovery HD
06
07
08
09

When I try to erase any of the last four partitions get "File system  resize support required" or "Couldn't modify partition table".  Trying  to verify the drive gives me "This disk doesn't contain an EFI system  partition". The "Erase free space" button is grayed out. The rEFIt  partitioning tool says "Status: Analysis inconclusive, will not touch  this disk. Error: Not Found returned from gptsync.efi"

Also, all partitions mentioned above are showing up in Finder, I guess that is not supposed to happen?

Gdisk output:

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00002DCF-4F07-0000-DB14-00001A000000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 2-sector boundaries
Total free space is 525817 sectors (256.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   0700  EFI system partition
   2          409640       138052343   65.6 GiB    AF00  Customer
   3       138052344       139321879   619.9 MiB   AF00  Recovery HD
   4       139321880       139731479   200.0 MiB   EF00  EFI System Partition
   5       139732992       148881847   4.4 GiB     0700  LINUX
   6       149143992       149145945   977.0 KiB   0700 
   7       149145946       228772899   38.0 GiB    0700 
   8       228772904       236715991   3.8 GiB     0700

Many thanks

---

### Post by tombaugh on 2012-04-09
My problem was more or less solved by deleting all partition but the  first two using GPT fdisk, and then resizing the OS X partition. The  only thing remaining is that EFI is visible under devices in Finder.

I think I'll wait a few weeks before attempting a new Ubuntu install...

---

