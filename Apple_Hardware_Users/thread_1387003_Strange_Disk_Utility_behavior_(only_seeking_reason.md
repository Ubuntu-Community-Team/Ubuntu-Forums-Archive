---
title: "Strange Disk Utility behavior (only seeking reason, not sln)"
date: 2010-01-21
forum: Apple Hardware Users
---

### Post by CovenStine on 2010-01-21
I installed a 300GB drive in my G4.
Disk utility saw it as a 300, and sees/uses all 500GB of the 500 I have as a hdb on the primary chain, so I used Disk Utility to erase/create partition table, repartition, reformat the disk.
Then, it wasn't mountable.  It showed up in the 'places' menu alright, and hdc is listed in Storage Device Manager, but there was no hdc1 or drop-down arrow.
It couldn't be mounted from Disk Utility either.
Whenever I try to mount it, I got this error:
```
 **Unable to mount location**
Error mounting:  mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
    missing codepage or helper program or other error
    In some cases useful info is found in syslog - try 
    dmesg|tail or so
```

I did some searching, and this info was useful to the folks helping to diagnose this issue on other systems:

```
home@FrontRoom:~$ sudo fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           149841797 @ 2018      ( 71.5G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 6457673 @ 149843815 (  3.1G)  Linux swap

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0
```

```
home@FrontRoom:~$ dmesg |tail -20
[   34.407465] lp: driver loaded but no devices found
[   34.489339] ppdev: user-space parallel port driver
[   36.956078] usb 1-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  905.701312] usb 1-1: USB disconnect, address 2
[  905.701825] usblp0: removed
[ 1089.948822] UDF-fs: No anchor found
[ 1089.948846] UDF-fs: Rescanning with blocksize 2048
[ 1090.148349] UDF-fs: No anchor found
[ 1090.148367] UDF-fs: No partition found (1)
[ 1090.221309] ISOFS: Unable to identify CD-ROM format.
[ 1669.120333] UDF-fs: No anchor found
[ 1669.120363] UDF-fs: Rescanning with blocksize 2048
[ 1669.372333] UDF-fs: No anchor found
[ 1669.372360] UDF-fs: No partition found (1)
[ 1670.200313] ISOFS: Unable to identify CD-ROM format.
[ 1715.488372] UDF-fs: No anchor found
[ 1715.488404] UDF-fs: Rescanning with blocksize 2048
[ 1715.800834] UDF-fs: No anchor found
[ 1715.800863] UDF-fs: No partition found (1)
[ 1716.400359] ISOFS: Unable to identify CD-ROM format.
```

Long story short, I installed gparted and re-did the partitioning and re-built the file system, aaand voila!  Success.

What’s the deal with Disk Utility?  Shouldn’t it have been able to complete that task just as accurately as gparted?

---

### Post by tom4everitt on 2010-01-22
Haha, yeah I know. Disk utility is acting a bit funny from time to time :) Usually its just to restart it or something, but sometimes its even worse... Thats why like having options I guess :)

---

