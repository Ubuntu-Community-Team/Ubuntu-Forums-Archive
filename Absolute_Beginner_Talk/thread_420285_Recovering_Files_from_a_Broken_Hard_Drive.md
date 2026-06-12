---
title: "Recovering Files from a Broken Hard Drive"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-04-23
A couple days ago I made a go at Dual Booting XP with Feisty. Had a bit of trouble, and I went back to just using Feisty alone. But when I got everything all set up again, it turns out my secondary hard drive won't mount anymore.

When I attempt to mount it, it says:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1, missing codepage or other error. In some cases useful info is found in syslog - try dmesg | tail or so
```

The output of dmesg | tail is
```
[  129.294141] usb 5-1: reset high speed USB device using ehci_hcd and address 4
[  129.494262] ndiswrapper: driver neta5agu (D-Link,05/08/2006,1.5.202.2) loaded
[  129.495390] ndiswrapper (ZwQueryValueKey:2568): not fully implemented (yet)
[  130.480336] wlan0: ethernet device 00:15:e9:2b:8b:3c using NDIS driver: neta5agu, version: 0x10005, NDIS version: 0x501, vendor: '', 2001:3A03.F.conf
[  130.480364] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  133.336164] NET: Registered protocol family 10
[  133.336435] lo: Disabled Privacy Extensions
[  141.418980] EXT3-fs: journal inode is deleted.
[  143.990319] wlan0: no IPv6 routers present
[  901.090178] EXT3-fs: journal inode is deleted.
```

Now I have no illusions about getting everything back, but there are a few files on that drive that are of reasonable importance to me, and I'd like to access them before I format the thing again.

so, 

a) is there a way I can get this thing mounted again?

b) if not, can you reccomend a file recovery tool?

---

### Post by Cypher on 2007-04-23
Do
```

dmesg | grep hd

```
and post the results..

Regards

---

### Post by sunexplodes on 2007-04-23
```
[   28.642851]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
[   28.642865]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
[   29.057967] hda: WDC WD400BB-75DEA0, ATA DISK drive
[   29.337472] hdb: Maxtor 6Y080L0, ATA DISK drive
[   29.948474] hdc: HL-DT-ST RW/DVD GCC-4521B, ATAPI CD/DVD-ROM drive
[   30.731204] hdd: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[   30.806230] hda: max request size: 128KiB
[   30.830946] hda: Host Protected Area detected.
[   30.838267] hda: Host Protected Area disabled.
[   30.838274] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   30.838280] hda: cache flushes not supported
[   30.838344]  hda: hda1 hda2 < hda5 >
[   30.877927] hdb: max request size: 128KiB
[   30.878075] hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[   30.878208] hdb: cache flushes supported
[   30.878262]  hdb: hdb1
[   30.907208] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   30.934061] hdd: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.174523] EXT3-fs: hda1: orphan cleanup on readonly fs
[   35.174591] EXT3-fs: hda1: 1 orphan inode deleted
[   51.363327] EXT3 FS on hda1, internal journal

```

---

### Post by ajgreeny on 2007-04-23
Dop you get a grub menu showing OK when you start and if so what happens when you select the disk/partition which you say is broken?
Have you tried using a live CD and looking in gparted to see if the partitions are still there on the disk.  If so try mounting it with the live CD instead of the way you are at the moment.  I don't know if it will make any difference, but if files are still there they must be recoverable, I would think.  If you have no grub menu come up try reinstalling grub and see if that helps.

---

### Post by sunexplodes on 2007-04-23
As I said, this is a secondary hard drive, it doesn't boot an OS, i use it for storage. Thus, it wouldn't show up in the grub menu.

---

### Post by Cypher on 2007-04-23
Try
```

sudo dumpe2fs /dev/hdb1

```
and post back the results. Hopefully this will show it as a valid/usable EXT2/3 partition.

Regards

---

### Post by sunexplodes on 2007-04-23
that command spit out an ENORMOUS amount of data, far too much to catch it all in my terminal window. Most of it was long strings of 7-digit numbers...

This part stood out though:

```
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          07edbeb0-3232-49eb-8418-35fad0817a57
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4685824
Block count:              9357854
Reserved block count:     467892
Free blocks:              8158291
Free inodes:              4550347
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1021
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Thu Apr 19 16:00:35 2007
Last mount time:          Sun Apr 22 15:56:36 2007
Last write time:          Sun Apr 22 16:27:14 2007
Mount count:              26
Maximum mount count:      23
Last checked:             Thu Apr 19 16:00:35 2007
Check interval:           15552000 (6 months)
Next check after:         Tue Oct 16 16:00:35 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      d004eddb-bf20-41b2-aa90-e0df26c0b98e
Journal backup:           inode blocks
Journal size:             128M

```

---

### Post by Cypher on 2007-04-23
OK, yeah you can ignore all the inode information. What you have there is enough to indicate that the partition is properly recognized as an EXT3 filesystem. The magic number all matches.

Try doing
```
e2fsck -y /dev/hdb1
```
to check/fix the partition and then try to remount it and see if you have better luck.

Regards

---

### Post by sunexplodes on 2007-04-23
Wonderful, will give it a try, thank you.

---

