---
title: "Optimizing disk drive performance."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-05
I ran hdparm /dev/hda and got the following:
```
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 312581808, start = 0

```

I saw another person's results:
```
/dev/hda:
multcount = 32 (on)
IO_support = 1 (32-bit)
unmaskirq = 1 (on)
using_dma = 1 (on)
keepsettings = 0 (off)
readonly = 0 (off)
readahead = 256 (on)
geometry = 4095/16/63, sectors = 4127760, start = 0
```
And wonder about some of the settings.

Notice multicount, IO_support, and unmasking, Would it be wise to change my setting?

---

### Post by Ramses de Norre on 2007-02-05
I think it's mostly trying.. This is mine: ```
ramses@icarus:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 312581808, start = 0

```
And I never had trouble with it, the multcount and unmaskirq are kind of tricky so I didn't risk my data to try them out.
To enable this I made this section in /etc/hdparm.conf:```
/dev/hda {
#       mult_sect_io = 16
#       write_cache = off
        dma = on
        io32_support = 3
}

```

---

### Post by Patrick K on 2007-02-06
Here is some more info re: the drives on my system. This data is from the Intel Application Accelerator (which provides 48bitLBA  functionality for W98, BIOS is 48bitLBA compliant, too). 
```
Device Information

          Primary Master:  ST3160023A
               Model:  ST3160023A
               Firmware:  8.01
               Device Type:  ATA - Fixed
               PIO Mode Support:  0 - 1 - 2 - 3 - 4
               DMA SW Mode Support:  No Support
               DMA MW Mode Support:  0 - 1 - 2
               UDMA Mode Support:  0 - 1 - 2 - 3 - 4 - 5
               LBA (28-bit maximum):  0x0FFFFFFF
               LBA (48-bit maximum):  0x000012A19EB1
               CHS:  FFFF x 0001 x 003F
               CHS Sectors:  0x003EFFC1
               Disk Size (28-bit maximum):  128.0 GB (137,438,952,960 bytes)
               Disk Size:  149 GB (160,041,886,208 bytes)
               Default Transfer Mode:  UDMA-5
               Current Transfer Mode:  UDMA-5
               Transfer Mode Limit:  No Limit
               Cable Type (Device):  80 Conductor
               Cable Type (Host):  80 Conductor
               PIO PPE:  Enabled
               UDMA Control Register:  Ultra DMA Mode Enabled
               UDMA Timing Register:  CT = 3 CLK / RP = 16 CLK
               Base Clock:  Ultra DMA 100 Timings


Secondary Master:  Maxtor 6L080L0
               Model:  Maxtor 6L080L0
               Firmware:  BAJ41G20
               Device Type:  ATA - Fixed
               PIO Mode Support:  0 - 1 - 2 - 3 - 4
               DMA SW Mode Support:  No Support
               DMA MW Mode Support:  0 - 1 - 2
               UDMA Mode Support:  0 - 1 - 2 - 3 - 4 - 5
               LBA (28-bit maximum):  0x098ABA00
               LBA (48-bit maximum):  0x0000098ABA00
               CHS:  3FFF x 0010 x 003F
               CHS Sectors:  0x00FBFC10
               Disk Size (28-bit maximum):  76.3 GB (81,964,302,336 bytes)
               Disk Size:  76 GB (81,964,302,336 bytes)
               Default Transfer Mode:  UDMA-5
               Current Transfer Mode:  UDMA-5
               Transfer Mode Limit:  No Limit
               Cable Type (Device):  80 Conductor
               Cable Type (Host):  80 Conductor
               PIO PPE:  Enabled
               UDMA Control Register:  Ultra DMA Mode Enabled
               UDMA Timing Register:  CT = 3 CLK / RP = 16 CLK
               Base Clock:  Ultra DMA 100 Timings


```This is the settings these drive are running with under Windows. 

Notice the Ultra DMA Mode Enabled. What about UDMA-5 mode. Is it possible to get this setting in Linux?

---

### Post by kerry_s on 2007-02-06
> **Patrick K said:**
> Here is some more info re: the drives on my system. This data is from the Intel Application Accelerator (which provides 48bitLBA  functionality for W98, BIOS is 48bitLBA compliant, too). 
```
Device Information

          Primary Master:  ST3160023A
               Model:  ST3160023A
               Firmware:  8.01
               Device Type:  ATA - Fixed
               PIO Mode Support:  0 - 1 - 2 - 3 - 4
               DMA SW Mode Support:  No Support
               DMA MW Mode Support:  0 - 1 - 2
               UDMA Mode Support:  0 - 1 - 2 - 3 - 4 - 5
               LBA (28-bit maximum):  0x0FFFFFFF
               LBA (48-bit maximum):  0x000012A19EB1
               CHS:  FFFF x 0001 x 003F
               CHS Sectors:  0x003EFFC1
               Disk Size (28-bit maximum):  128.0 GB (137,438,952,960 bytes)
               Disk Size:  149 GB (160,041,886,208 bytes)
               Default Transfer Mode:  UDMA-5
               Current Transfer Mode:  UDMA-5
               Transfer Mode Limit:  No Limit
               Cable Type (Device):  80 Conductor
               Cable Type (Host):  80 Conductor
               PIO PPE:  Enabled
               UDMA Control Register:  Ultra DMA Mode Enabled
               UDMA Timing Register:  CT = 3 CLK / RP = 16 CLK
               Base Clock:  Ultra DMA 100 Timings


Secondary Master:  Maxtor 6L080L0
               Model:  Maxtor 6L080L0
               Firmware:  BAJ41G20
               Device Type:  ATA - Fixed
               PIO Mode Support:  0 - 1 - 2 - 3 - 4
               DMA SW Mode Support:  No Support
               DMA MW Mode Support:  0 - 1 - 2
               UDMA Mode Support:  0 - 1 - 2 - 3 - 4 - 5
               LBA (28-bit maximum):  0x098ABA00
               LBA (48-bit maximum):  0x0000098ABA00
               CHS:  3FFF x 0010 x 003F
               CHS Sectors:  0x00FBFC10
               Disk Size (28-bit maximum):  76.3 GB (81,964,302,336 bytes)
               Disk Size:  76 GB (81,964,302,336 bytes)
               Default Transfer Mode:  UDMA-5
               Current Transfer Mode:  UDMA-5
               Transfer Mode Limit:  No Limit
               Cable Type (Device):  80 Conductor
               Cable Type (Host):  80 Conductor
               PIO PPE:  Enabled
               UDMA Control Register:  Ultra DMA Mode Enabled
               UDMA Timing Register:  CT = 3 CLK / RP = 16 CLK
               Base Clock:  Ultra DMA 100 Timings


```This is the settings these drive are running with under Windows. 

Notice the Ultra DMA Mode Enabled. What about UDMA-5 mode. Is it possible to get this setting in Linux?

For udma5 it would be> sudo hdparm -X69 /dev/hd?

---

### Post by Patrick K on 2007-02-06
Thanks for the reply. I tried it and "hdparm Tt" returned slower time with X69 than X_. I'll leave it at the default, I guess.

---

