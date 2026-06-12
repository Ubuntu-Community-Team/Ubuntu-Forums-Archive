---
title: "[SOLVED] ubuntu has my IDE drives as SATA drives!!"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by 720iD on 2007-12-18
during the install of ubuntu my ide harddrives have been labeled as sata drives by the install process, what would be the reason for this? will it cause me any problems in future? can it be corrected?

---

### Post by philinux on 2007-12-18
Feisty had mine as IDE. I installed gutsy and got sata. 

No problems at all just nomenclature change from hda to sda no worries.

---

### Post by hyper_ch on 2007-12-18
the only problem you could have if you have ide and sata drives together... on my system grub behaves a bit strangely because of that (I need to manually set the (hdX,Y) right when I install a new kernel.

---

### Post by thelatinist on 2007-12-18
Ubuntu now uses some sort of generic driver for hard disk drives.  All drives appear as sd* instead of hd*, even IDE drives.  It shouldn't cause you any problems.

---

### Post by 720iD on 2007-12-18
thanks all!:KS

i shall leave this thread open for a while before i mark it solved.

---

### Post by coffeecat on 2007-12-18
Others have already explained, but the specific reason is the use of the libata drivers in the kernel. This has been going on since the 2.6.19 kernel and has affected other distros too. You might find [this link]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce") explains it better than I can.

I guess the Ubuntu devs are compiling both the old ATA drivers and the libata drivers into the kernel, because in my AMD64/VIA chipset desktop box, the hard drive appears as hda, whereas in my Intel/Intel laptop, the ide drive appears as sda. Ho hum. Keeps life interesting I suppose. :)

---

### Post by jayson.rowe on 2007-12-18
Since Linux 2.6.22 all drives will be known as SDA rather than HDA...all distros.

---

