---
title: "Incorrect HD detection in feisty"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by joco2 on 2007-03-28
Hi I'm a relative newbie, I have been using ubuntu 6.10 for a while and upgraded to the beta version of fiesty, (clean install off the live cd). Runs great and i have no major problems, just little annoying ones. 

My drive partitions no longer show up on the desktop, in the places menu or in nautilis. The display volumes is ticked in config. and the volumes appear as they should as folders under /media/ and i have access to these folders. In my search for a solution i noticed that on installing fiesty my hd has been detected as a SCSI drive but it's an ATA6 so now i see sda instead of hda. I am not sure if this is part of the problem because the drive seems to work fine.

How do I change it from sda (SCSI) to hda? can i do this without re-installing.

The only other thing i have found annoying is that network-manager always asks me for a password to connect. but i can live with that.

Any help would be appreciated

Cheers

---

### Post by procras on 2007-03-28
My drives on IDE interface are hda hdb etc

My drives on SATA interface are sda sdb etc.

If your drives are connected by the SATA interface they should be sda etc.

---

### Post by n1ywb on 2007-03-29
Ditto this problem. I know for a fact my HD is PATA and not SATA however feisty has attached it to /dev/sda instead of /dev/hda. My system HAS an SATA controller but nothing is connected to it. Seems to be a kernel issue. Here is some of my dmesg output:

```

***
[   18.038488] SCSI subsystem initialized
[   18.045518] libata version 2.20 loaded.
***
[    4.336000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.336000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    4.336000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.336000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011410 irq 14
[    4.336000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011418 irq 15
[    4.336000] scsi0 : ata_piix
[    4.500000] ata1.00: ATA-6: TOSHIBA MK6006GAH, BZ001K, max UDMA/100
[    4.500000] ata1.00: 117210240 sectors, multi 16: LBA48
[    4.508000] ata1.00: configured for UDMA/100
[    4.508000] scsi1 : ata_piix
[    4.508000] ata2: port disabled. ignoring.
[    4.508000] ata2: reset failed, giving up
[    4.508000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6006GA BZ00 PQ: 0 ANSI: 5
[    4.508000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.508000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.664000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[    4.664000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.664000] ata3: SATA max UDMA/133 cmd 0x000114b8 ctl 0x0001140e bmdma 0x000114a0 irq 18
[    4.664000] ata4: SATA max UDMA/133 cmd 0x000114b0 ctl 0x0001140a bmdma 0x000114a8 irq 18
[    4.664000] scsi2 : ata_piix
[    4.820000] ATA: abnormal status 0x7F on port 0x000114bf
[    4.824000] scsi3 : ata_piix
[    4.980000] ATA: abnormal status 0x7F on port 0x000114b7
***
[    5.076000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    5.076000] sda: Write Protect is off
[    5.076000] sda: Mode Sense: 00 3a 00 00
[    5.076000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.076000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    5.076000] sda: Write Protect is off
[    5.076000] sda: Mode Sense: 00 3a 00 00
[    5.076000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.076000]  sda: sda1 sda2 sda3
[    5.116000] sd 0:0:0:0: Attached scsi disk sda
[    5.120000] sd 0:0:0:0: Attached scsi generic sg0 type 0
***

```

---

### Post by dwblas on 2007-04-10
Same problem here.  I don't have any SATA drives.  I did two things 
[1] switched back to kernel 2.6.20-12
[2] changed /etc/fstab to use /dev/hda6, etc instead of the UUID
Take your pick as to which corrected the problem, but I would bet on the kernel.  This is why we test.

---

