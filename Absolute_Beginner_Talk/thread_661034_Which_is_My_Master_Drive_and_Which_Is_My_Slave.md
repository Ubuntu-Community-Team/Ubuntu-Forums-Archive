---
title: "Which is My Master Drive and Which Is My Slave?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-07
Does my master drive appear as hda and my slave as hdb? Thanks for clearing this up for me.

---

### Post by eluzi on 2008-01-07
Exactly. It means your drives are IDE, they are both under the some IDE controller, hda is master and hdb is slave.

Examples below:

    * /dev/fd0 - First floppy unit

    * /dev/fd1 - Second floppy

    * /dev/hda - (primary master IDE drive)

    * /dev/hda1 - primary partition of hda

    * /dev/hdb - (primary slave).

    * /dev/hdb1 - primary partition of hdb

    * /dev/sda - primary SCSI drive

    * /dev/sda1 - primary partition of sda

    * /dev/sdb - second SCSI drive

    * /dev/sdb1 - primary partition of sdb

    * /dev/sr0 - primary SCSI cdrom

---

### Post by LaRoza on 2008-01-07
For future reference, Ubuntu  calls all storage devices "sdx", even when they are not SCSI.

---

