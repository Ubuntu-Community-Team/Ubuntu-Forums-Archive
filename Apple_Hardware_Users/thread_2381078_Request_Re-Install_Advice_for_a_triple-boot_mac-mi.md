---
title: "Request Re-Install Advice for a triple-boot mac-mini"
date: 2017-12-26
forum: Apple Hardware Users
---

### Post by k3nden on 2017-12-26
I have a mac-mini that triple boots OSX/WIn10/and 1604 Ubuntu.  I have broken WiFi in Ubuntu and spent way to many hours trying to correct the problem with no luck. I want to start over with a new install of Ubuntu but do not want to break the other partitions.

Originally I installed Ubuntu using USB.  The disk is partitioned as shown below: 
```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6BDBBC92-5972-4200-AEA4-F3B03F303FA2


Device          Start        End   Sectors   Size Type
/dev/sda1          40     409639    409600   200M EFI System
/dev/sda2      409640  406038023 405628384 193.4G Apple HFS/HFS+
/dev/sda3   406300168  494962151  88661984  42.3G Microsoft basic data
/dev/sda4   495224296  496493831   1269536 619.9M Apple HFS/HFS+
/dev/sda5   496494592 1225009151 728514560 347.4G Microsoft basic data
[B]/dev/sda6  1225009152 1256 259583  31250432  14.9G Linux swap
/dev/sda7  1256259584 1953523711 697264128 332.5G Linux filesystem[/B]


```
Before I did, I wanted to check to see what i should expect doing a re-install from the USB.
Will it affect reFind  and cause problems booting either win10 or OSX?
Should I expect the re-install only to affect sda7?

---

### Post by kevin160 on 2017-12-27
Things _can_ go wrong, so definitely make sure to do a backup of everything (macOS, Windows and Linux).  

Usually, your Ubuntu will have installed it's grub onto your EFI partition.  In Ubuntu, df your drive, and you should see your /dev/sda1 mounted under /boot/efi.  If it isn't this way, you may have installed grub to your Linux root partition, which is also ok.  When you reinstall, make sure it configures it's grub to be the same as now.  

Other than that, it should go smoothly.  If it boots straight into grub instead of going through rEFInd, reboot, hold OPT, and select rEFInd while holding CTRL, and you should be back to normal.

---

