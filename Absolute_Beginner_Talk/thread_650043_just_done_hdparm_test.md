---
title: "just done hdparm test"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-25
ok i have 2 drive

sda = 7,200RPM SATA 8MB Cache
sdb = 10,000RPM SATA 16MB Cache <--brand new

```


/dev/sda1:
 Timing buffered disk reads:  152 MB in  3.01 seconds =  50.48 MB/sec
scott@scott-desktop:~$ sudo hdparm -t /dev/sdb1

/dev/sdb1:
 Timing buffered disk reads:   96 MB in  3.04 seconds =  31.58 MB/sec


```

yet my faster drive is slower!?

why is this?

---

### Post by Cypher on 2007-12-26
Show us the output of
```

hdparm -i /dev/sda
hdparm -i /dev/sdb
dmesg | grep sd[ab]

```

Perhaps DMA is turned off for SDB and that's why it slower..at 10k, the performance should be significantly faster than the 7200 RPM drive..

---

### Post by skymera on 2007-12-27
ok i'll do in a few days.

im out atm so only got my lappy.

thanks :)

---

### Post by skymera on 2007-12-29
ok SDA

```

scott@scott-desktop:~$ hdparm -i /dev/sda
/dev/sda: Permission denied
scott@scott-desktop:~$ sudo hdparm -i /dev/sda
[sudo] password for scott:

/dev/sda:

 Model=WDC WD1600JS-75NCB3                     , FwRev=10.02E04, SerialNo=     WD-WCANM8312488
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

SDB

```

scott@scott-desktop:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC WD1500ADFD-00NLR5                   , FwRev=21.07QR5, SerialNo=     WD-WMAP41845363
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=48
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 published, ANSI INCITS 397-2005:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

scott@scott-desktop:~$ 

```

Dmesg SDA

```

scott@scott-desktop:~$ dmesg | grep sda
[   25.461272] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   25.461284] sd 0:0:0:0: [sda] Write Protect is off
[   25.461286] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.461300] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.461871] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   25.461880] sd 0:0:0:0: [sda] Write Protect is off
[   25.461882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.461896] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.461899]  sda: sda1
[   25.468788] sd 0:0:0:0: [sda] Attached SCSI disk
scott@scott-desktop:~$ 

```

Dmesg SDB
```

scott@scott-desktop:~$ dmesg | grep sdb
[   25.468935] sd 1:0:0:0: [sdb] 293046768 512-byte hardware sectors (150040 MB)
[   25.468944] sd 1:0:0:0: [sdb] Write Protect is off
[   25.468946] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.468959] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.468992] sd 1:0:0:0: [sdb] 293046768 512-byte hardware sectors (150040 MB)
[   25.469000] sd 1:0:0:0: [sdb] Write Protect is off
[   25.469002] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.469015] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.469017]  sdb:<6>e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:27:14:ca
[   25.477206]  sdb1 sdb2 sdb3 < sdb5 >
[   25.491832] sd 1:0:0:0: [sdb] Attached SCSI disk
[   30.198153] Adding 979956k swap on /dev/sdb2.  Priority:-1 extents:1 across:979956k
[   76.771523] EXT3 FS on sdb1, internal journal
scott@scott-desktop:~$ 

```

any clues?
and whats DMA?

---

### Post by asmiller-ke6seh on 2007-12-29
DMA = Direct Memory Access: The following, from Wikipedia ...
[COLOR="Navy"]
DMA is an essential feature of all modern computers, as it allows devices to transfer data without subjecting the CPU to a heavy overhead. Otherwise, the CPU would have to copy each piece of data from the source to the destination. This is typically slower than copying normal blocks of memory since access to I/O devices over a peripheral bus is generally slower than normal system RAM. During this time the CPU would be unavailable for any other tasks involving CPU bus access, although it could continue doing any work which did not require bus access.

A DMA transfer essentially copies a block of memory from one device to another. While the CPU initiates the transfer, it does not execute it. For so-called "third party" DMA, as is normally used with the ISA bus, the transfer is performed by a DMA controller which is typically part of the motherboard chipset. More advanced bus designs such as PCI typically use bus mastering DMA, where the device takes control of the bus and performs the transfer itself.

A typical usage of DMA is copying a block of memory from system RAM to or from a buffer on the device. Such an operation does not stall the processor, which as a result can be scheduled to perform other tasks. DMA transfers are essential to high performance embedded systems. It is also essential in providing so-called zero-copy implementations of peripheral device drivers as well as functionalities such as network packet routing, audio playback and streaming video.[/COLOR]

---

### Post by skymera on 2007-12-29
ok thanks for clearing that up.

from what i read it helps a lot.


anyeay from my post any reason my Raptor is getting slower than my standard drive?

---

### Post by skymera on 2007-12-29
anyone else?

---

### Post by skymera on 2007-12-30
seems hdparm is highly inaccurate read below

sudo hdparm -Tt /dev/sdb (timing chached them buffered reads on raptor)

```

/dev/sdb:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.06 MB/sec
 Timing buffered disk reads:  234 MB in  3.00 seconds =  77.88 MB/sec

```

NOW

sudo hdparm -t /dev/sdb (only testing buffered reads on the SAME drive )

```

cott@scott-desktop:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:   78 MB in  3.10 seconds =  25.13 MB/sec
scott@scott-desktop:~$ 

```

how can the same test on the same drive has VERY different results?

---

### Post by aktiwers on 2007-12-30
Or try do this on both drives:
```
 sudo hdparm -X34 -d1 -u1 /dev/YOURDISC
``````
sudo hdparm -c3 -m16 /dev/YOURDISC
```Or read here first
[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance]("http://ubuntuforums.org/showthread.php?t=312707")

---

### Post by skymera on 2007-12-30
/dev/sda

```

scott@scott-desktop:~$  sudo hdparm -X34 -d1 -u1 /dev/sda
[sudo] password for scott:

/dev/sda:
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting xfermode to 34 (multiword DMA mode2)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error
scott@scott-desktop:~$ sudo hdparm -c3 -m16 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
 IO_support    =  0 (default 16-bit)
scott@scott-desktop:~$ 


```

sdb

```

scott@scott-desktop:~$  sudo hdparm -X34 -d1 -u1 /dev/sdb

/dev/sdb:
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting xfermode to 34 (multiword DMA mode2)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error
scott@scott-desktop:~$ sudo hdparm -c3 -m16 /dev/sdb

/dev/sdb:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
 IO_support    =  0 (default 16-bit)
scott@scott-desktop:~$ 

```

dosent loook right to me =S

---

### Post by aktiwers on 2007-12-30
Try trouble-shooting here
[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

This was the link I meant to give you above.

Sorry I cant be off more help, my best guess would be your disc didnt support it, though I doubt it if the discs are not too old.

---

### Post by LittleLion on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/147858](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/147858) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have same problem too.

Look:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/147858](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/147858)

and:
[http://inferno.slug.org/cgi-bin/wiki?action=browse&id=Western_Digital_NCQ](http://inferno.slug.org/cgi-bin/wiki?action=browse&id=Western_Digital_NCQ)

---

