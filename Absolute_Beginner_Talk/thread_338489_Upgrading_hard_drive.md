---
title: "Upgrading hard drive?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-01-14
Hello All

The P4 desktop computer with Xubuntu has a 20Mb hard drive. I'm using large chunks of this and can see the need to upgrade quite soon. The local computer shop has PATA and SATA hard drives. What do I buy?

lshw gives the following info on the current hard drive...

```
              *-disk
                   description: ATA Disk
                   product: WDC WD200BB-00DGA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 05.03E05
                   serial: WD-WCADK3686929
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
```

Thanks

---

### Post by cilynx on 2007-01-14
If you alredy have a SATA controller on your machine, SATA is pretty nice.  It's faster and a little more convenient to plug in.  It's not a huge improvement to the standard user however.  You already have a PATA controller in your system for sure, so that's always safe.  It won't be much slower and it's guaranteed to work.  Basically, if you want the newest wizbang, get SATA.  If you prefer it Just Works, get PATA.

---

### Post by moshuptrail on 2007-01-14
The point is, to use a SATA drive you need a SATA interface.
Since your desktop has a 20G now, I'm guessing it's a few years old and probably does not support SATA.  (Serial ATA)   The good news is, you can get a real deal on a simple ATA compatible drive.  I just picked up a 200G Maxtor on eBay for $60.  (similar problem)

---

### Post by keithpeter on 2007-01-14
> **moshuptrail said:**
> The point is, to use a SATA drive you need a SATA interface.
Since your desktop has a 20G now, I'm guessing it's a few years old and probably does not support SATA. 

Yup - PATA it is, I've just been googling. Thanks both

Cheers

---

