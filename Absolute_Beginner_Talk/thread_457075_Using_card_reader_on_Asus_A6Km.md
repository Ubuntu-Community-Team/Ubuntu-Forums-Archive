---
title: "Using card reader on Asus A6Km"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by audunmb on 2007-05-28
How to use the card reader?

It seems to me that Ubuntu recognises the card reader as the the Hardware manager lists it as Vendor: Ricoh Co Ltd, Device: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter, but I can't figure out how to use it. Shouldn't it be listed with the other drives?

I've searched the forums and the documentation, but I didn't find anything.

---

### Post by maple03 on 2007-05-30
I Have the same problem on A8jn. This is all I get:

06:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:00.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

06:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1447
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:00.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1447
        Flags: bus master, medium devsel, latency 0, IRQ 5
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1447
        Flags: medium devsel, IRQ 5
        Memory at feafec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1447
        Flags: medium devsel, IRQ 5
        Memory at feafe800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2


# lsmod |egrep '(sdhci|mmc)'
mmc_block              13832  0 
sdhci                  18700  0 
mmc_core               26756  2 mmc_block,sdhci

# ls /dev/mmc*
ls: /dev/mmc*: No such file or directory

And nothing in dmesg when I insert a MMC-card. I tried to boot with the card inserted, but that gave no results too. Can someone help me?

---

### Post by Inxsible on 2007-05-30
I have the exact same card reader from Ricoh. 
 
I have read that if it is from Texas Instruments, you can install a package called tifm *****
 
cant recollect the exact name now. I did install that package in hope, that it will work, but have been unsuccessful. Maybe I did something wrong.
 
Will have to look into it more.
 
Until then, if someone knows how to have the Ricoh ones recognized, it will be gr8 !!!

---

