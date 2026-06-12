---
title: "Beige G3, quik, and ATA drives"
date: 2005-05-18
forum: Apple PPC Users
---

### Post by linutic on 2005-05-18
Anyone have any data indicating if Open Firmware 2.0f1 in a Rev. A Beige G3 is capable of booting Quik off of an ATA drive? I've found reports of people using ATA drives with quik on other systems, and with SCSI drives on Beiges, but not ATA on a Beige. I've fiddled extensively with load-base and boot-device settings, but - although OS 9 boots perfectly off if this ATA drive - I cannot get Open Firmware to acknowledge that it's anything more than connected. 

Randomly, after running the System Disk extension, I'm now (unlike before) presented with a huge dump from the nvramrc when I execute 'printenv' within OF.

Of note are these entries (although I have no idea precisely what they serve to indicate):

$E
dev ide0
:open use-ata-interface 0 +c -1
:set-device-id set-drive-select
:reset-atapi-bus reset-ata-bus
' reset-ata-bus 2c + ' 2 $L

---and---

When I execute dev / ls, I see (among others):

FF83C928        /ide@20000       (heathrow-ata)
FF83E680       /disk@0,0

Can anyone make sense of any of this, and possibly explain why
1)  it staunchly refuses to 'OPEN' /pci/mac-io/ide@20000/disk@0,0 or ...disk@0:0
and/or
2) it's still, somehow, able to boot MacOS 9.1 off of this same bloody drive using /AAPL,ROM

Many thanks!

---

