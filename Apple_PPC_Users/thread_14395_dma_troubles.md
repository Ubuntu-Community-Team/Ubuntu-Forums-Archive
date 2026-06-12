---
title: "dma troubles"
date: 2005-02-07
forum: Apple PPC Users
---

### Post by clarknova on 2005-02-07
Hi,

My hdd is running v e r y   s l o w  l   y. Dang. Check it out:

> root@chico:/home/david # hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:    4 MB in  3.17 seconds =   1.26 MB/sec

I used to get ~20 MB/sec with this exact same hardware. I'm not sure what changed.

It appears that my hdd won't run in dma mode, although it should:

> root@chico:/home/david # hdparm /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19386/16/63, sectors = 19541088, start = 0

I tried turning on dma mode:
> 
root@chico:/home/david # hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

but that tended to cause things to freeze up momentarily, and hdparm revealed that dma was soon switched off again, which is probably the only reason we didn't freeze permanently.

I also get this occasionally: 
> 
david@chico:~ $ sudo hdparm -t /dev/hda

/dev/hda:

ide-pmac lost interrupt, dma status: a480

So I checked the boot messages:
> 
root@chico:/home/david # dmesg | grep hda
hda: WDC WD100BA, ATA DISK drive
hda: Enabling Ultra DMA 2
hda: max request size: 128KiB
hda: 19541088 sectors (10005 MB) w/1961KiB Cache, CHS=19386/16/63, UDMA(33)
Adding 589832k swap on /dev/hda4.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hda: Set PIO timing for mode 0, reg: 0x1090032b
hda: lost interrupt
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
hda: lost interrupt
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
hda: lost interrupt
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
hda: lost interrupt
hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
hda: DMA disabled
hda: Enabling Ultra DMA 2

---repeated---

and that's when things get really over my head. It appears to me that the kernel is recognizing that my hdd is ATA-33 and putting it into dma mode, but then changes that at some point. I haven't been able to find much about this on Google.

Any ideas? Thanks a bunch!

System:

iMac 350 MHz
Ununtu Warty Warthog
Western Digital 10 GB hard drive, ATA-33

---

### Post by clarknova on 2005-02-09
So after a reboot, hdparm was showing 20 MB/s, as it should with this hdd. I might be tempted to say the hdd is toast, but this machine has a very peculiar pattern in the past month or so of working fine for about a day and a half, then this type of thing. A reboot usually or always corrects it for a little while, which makes me think there is something funny going on in the kernel or some such place.

 :confused:

---

### Post by khc on 2005-02-10
> hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }

I remember seeing something similar on a PC a couple years ago, replaced the disk and it disappeared. I did not try to benchmark before/after speed though.

---

