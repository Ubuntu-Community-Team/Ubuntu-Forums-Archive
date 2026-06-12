---
title: "recognising my disk wrongly"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by mechmg93 on 2007-05-15
i just installed ubuntu feisty. my problem is that my ata disk is recognised as scsi, though it isn't  and the partitions are /dev/sda1 etc. 

this is the first time my disk is recognised this way. normally the partitions should be /dev/hda1 etc. 

do you have any idea what went wrong??

---

### Post by Kobalt on 2007-05-15
Ubuntu 7.04 is now using an improved version of libata, it's a normal thing that you see your drives as sda and not hda :)

---

### Post by annda on 2007-05-15
it looks like sata disks use the scsi driver with the latest kernels. i've had this with other current linux distributions.

does this cause any problems? can you mount all your disks/partitions? do you need help with configuration? or are the names just confusing?

---

