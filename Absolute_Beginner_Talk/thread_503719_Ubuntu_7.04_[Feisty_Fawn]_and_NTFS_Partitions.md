---
title: "Ubuntu 7.04 [Feisty Fawn] and NTFS Partitions"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by soso.ro on 2007-07-18
I have this system:

MB:                 Shuttle AK32A  (5 PCI, 1 AGP, 2 SDR DIMM, 2 DDR DIMM, Audio)
                       AMD Athlon XP, 1533 MHz (11.5 x 133) 1800+
Video:             NVIDIA GeForce4 MX 440   (64 MB)
RAM:              2 x  256 MB
HDD:               WDC WD2500JB-00REA0  (232 GB, IDE)
DVDRW:          PIONEER DVD-RW  DVR-106D
Network:        2 x SURECOM EP-320X-R 100/10/M PCI Adapter
Monitor:          Samsung SyncMaster 710N [17" LCD] 
TV Tuner:        PCI Leadtek WinFast TV2000 XP Expert (PAL)
USB:                Bluetooth Dongle
USB:                Hercules DJ Console


On my harddrive i got 3 partitions:
c: 38468  NTFS [Windows]
d: 99998 NTFS [Documents]
e: 99998 NTFS [Others]

How can i install Ubuntu 7.04 without losing my [d:] and [e:] stuff?
Can i find drivers for my hardware (TV Tuner, Bluetooth, DJ Console)?

---

### Post by AlexenderReez on 2007-07-18
> **soso.ro said:**
> I have this system:



On my harddrive i got 3 partitions:
c: 38468  NTFS [Windows]
d: 99998 NTFS [Documents]
e: 99998 NTFS [Others]

How can i install Ubuntu 7.04 without losing my [d:] and [e:] stuff?
Can i find drivers for my hardware (TV Tuner, Bluetooth, DJ Console)?


hm...just install it....delete c partition(if you don't want windows anymore...then make ext3 partition about 37468 and swap = 1g(since your ram is standard but actually the best swap partition is 512mb --> 1g)...

how to?search in google or tutorials and tips section,ubuntu forums

---

