---
title: "has anyone gotten sata dma to work?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-02
Running the latest version of ubuntu with all updates including the latest kernel for dapper trying to get dma enabled on a sata drive and it's not working

john@ubuntu:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

I did a search for this problem and i found alot of people patching there kernel to get dma support for a sata drive but that was for the older kernels

---

### Post by halfvolle melk on 2006-07-02
After some Sherlocking I found this:
[http://www.ubuntuforums.org/archive/index.php/t-61075.html](http://www.ubuntuforums.org/archive/index.php/t-61075.html)

> If your disk is showing up as /dev/sda, then DMA is already enabled. No need to fiddle with it.
 
 -ml
 (hdparm author)

Also, you can check your dmesg. Here's a bit of mine:
```
[17179575.384000] ata2: dev 0 configured for UDMA/133
[17179575.388000] sata_get_dev_handle: SATA dev addr=0x70000, handle=0xdffd96c0
[17179575.396000] scsi1 : sata_nv
[17179575.396000]   Vendor: ATA       Model: SAMSUNG SP2504C   Rev: VT10
[17179575.396000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.396000] **** SET: Misaligned resource pointer: dea86f42 Type 07 Len 0
[17179575.396000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[17179575.396000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 225
[17179575.396000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179575.396000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xC400 irq 225
[17179575.396000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xC408 irq 225
```
I'm not sure what it means but it does say dma a lot :)

---

