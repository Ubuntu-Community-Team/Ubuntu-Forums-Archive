---
title: "Asus K61IC and OCZ-Vertex3"
date: 2012-10-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by disik on 2012-10-05
Asus K51IC with the latest BIOS 210, SSD OCZ Vertex3 with the latest firmware version 2.22, Ubuntu 12.04 64 bit with latest updates.
When writing to SSD the following messages appear in dmesg:```
[ 6178.480251] ata1: exception Emask 0x10 SAct 0x0 SErr 0x1810000 action 0xe frozen
[ 6178.480259] ata1: irq_stat 0x00400000, PHY RDY changed
[ 6178.480265] ata1: SError: { PHYRdyChg LinkSeq TrStaTrns }
[ 6178.480274] ata1: hard resetting link
[ 6179.204171] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 6179.225547] ata1.00: configured for UDMA/33
[ 6179.225561] ata1: EH complete
[ 6886.275680] ata1: exception Emask 0x10 SAct 0x0 SErr 0x1990000 action 0xe frozen
[ 6886.275685] ata1: irq_stat 0x00400000, PHY RDY changed
[ 6886.275688] ata1: SError: { PHYRdyChg 10B8B Dispar LinkSeq TrStaTrns }
[ 6886.275694] ata1: hard resetting link
[ 6886.996174] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 6887.017082] ata1.00: configured for UDMA/33
[ 6887.017094] ata1: EH complete
```Lots of them.
I've googled this problem and the solutions were to replace the PSU or replace the SATA-cable. None of these can work with a laptop.
What can I do to get rid of these disconnects/reconnects on my laptop? Leaving thing like this will lead to data loss.

---

