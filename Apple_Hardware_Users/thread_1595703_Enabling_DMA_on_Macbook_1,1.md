---
title: "Enabling DMA on Macbook 1,1"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by Steve W. M. on 2010-10-13
Hi all, 

I am the noobiest of noobs. I'm running Ubuntu Lucid on a first-generation white Macbook (a 2006 model). My CD ripping is extremely slow and unreliable, and the ripped tracks are always choppy. Evidently I need to enable DMA, but having searched dozens of threads and spent many hours reading what documentation I could find, I have not come across any instructions that I both understand and can carry out.  

I did find a couple of help docs about DMA, but none of them were specific to my hardware, and the one Ubuntu help doc that I did find about running Lucid on Macbook 1,1 listed CD/DVD issues as "undocumented". 

There is also (evidently) the  possible issue of SCSI emulation, which I also know nothing about. But every thread I've stumbled across focuses on enabling DMA.

When I type "sudo hdparm -I /dev/scd0", I get this:

```
ATAPI CD-ROM, with removable media
    Model Number:       MATSHITACD-RW  CW-8221                  
    Serial Number:      
    Firmware Revision:  GA0H    
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
    CBLID- above Vih
    Device num = 0

```I hope that is helpful. I apologize for my noobness, and for the fact that this thread may not exactly be very useful to anyone else.

---

### Post by Steve W. M. on 2010-10-13
Update:

I have noticed that typing just "hdparm /dev/sr0" gives me this:

```

multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```Been reading up, but so far I have no idea -- in practical terms --  what that ioctl message means.

---

### Post by bodhi.zazen on 2010-10-13
*Thread moved to **Apple Users**.*

---

### Post by logandzwon on 2010-10-14
I'm sure I agree with this thread being moved to Apple. His problem is not related to it being Apple. It's just a standard drive.

---

### Post by Steve W. M. on 2010-10-14
> 
I'm sure I agree with this thread being moved to Apple. His problem is  not related to it being Apple. It's just a standard drive.     
logangzwon, did you mean that you* weren't* sure? ;)

By the way, I ran top while running cdparanoia, and my cpu usage was about 2%. Maybe DMA is irrelevant here?

---

### Post by Steve W. M. on 2010-10-15
I hadn't realized that nearly every cd-ripping application for Ubuntu used cdparanoia. I tried ripping with just cdparanoia, and used the -Z flag to turn paranoia off completely (I don't think that you can pass that option to cdparanoia via, e.g., abcde). The rip went perfectly; no hanging, and no skips in the ripped tracks.

I guess my drive must be fairly reliable -- as my imported music sounds fine -- but that it was doing something to convince cdparanoia otherwise. Not a clue what it might have been.

Any ideas?

Update: Ripped a couple more CD's. Though they weren't in bad condition at all, there were skips this time. Someone please recommend something.

---

### Post by Steve W. M. on 2010-10-17
Marking thread as solved. 

DMA must not be the issue. I suppose I'll start a new thread when I have a clearer idea what I should be asking. Sorry for any inconvenience.

---

