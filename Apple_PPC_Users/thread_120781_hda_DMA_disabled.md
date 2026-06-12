---
title: "hda: DMA disabled"
date: 2006-01-23
forum: Apple PPC Users
---

### Post by ristosu on 2006-01-23
Sometimes, at boot, I get this:
<  /dev/ide/host0/bus0/target0/lun0:<3>ide-pmac lost interrupt, dma status: 8880
< hda: lost interrupt
< hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
< 
< hda: dma_intr: status=0xd0 { Busy }
< 
< hda: DMA disabled
< ide0: reset: success

sometimes only this:
>  /dev/ide/host0/bus0/target0/lun0:<3>ide-pmac lost interrupt, dma status: 8880
> hda: lost interrupt
> hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
> 

A third variant is:
>  /dev/ide/host0/bus0/target0/lun0:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
> hda: dma_intr: error=0x84 { DriveStatusError BadCRC }

None of them seems quite right to me. However, the latter two keep DMA enabled, resulting in a faster machine (even though 'dparm -i' says mdma2 in both cases).

The machine is a beige G3/233 rev A, and the disk is a IBM-DTLA-307030. I'm using quik for booting. The kernel is of version 2.6.8.1.

It's worth mentioning that the machine boots slowly. Already getting anything (quik boot prompt) on the screen after the chime takes 35 s. I wonder what's it doing, counting its memory (384 MB)?

---

