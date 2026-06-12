---
title: "Installation gone horribly wrong"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2006-01-12
Last night I installed Ubuntu onto my laptop. I said the installer to resize my second NTFS partition, but afterwards, it threw an error about "not able to resize" and another one that caused the installation to stop. "No biggie" I thought, I'll resize them manually. However, after the failed installation, "No Operating System Found" appeared on my screen. Throwing some Emergency Boot Disc at it, I'm now pretty sure my partition tables got wiped (well, whole my MBR, as GRUB wasn't booted too). There were 2 NTFS partitions, 1 FAT32 and 1 Ext3.

Is there any chance I can recover them? :'(
Also note I can't put the hdd in another computer (I have no laptop disassembly skills and no laptopHDD-to-desktopHDD connector) and I don't have a floppy drive.

You would **greatly** help me with this. I"m almost begging for help. :(

---

### Post by daschl on 2006-01-12
hmmm so with a live cd you can't access the partitions at all?

(did you boot knoppix or ubuntu?)

yes, it is possible that you mess up your partition table during the partition process. did you try to install ubuntu again?

---

### Post by Nanaki on 2006-01-12
GParted won't start due to a segmentation fault. I tried Puppy Linux and Ubuntu Live but both won't configure my Wireless Adapter, so I can't really download more packages.

The Ubuntu installer also reports about one unformatted disc.

---

