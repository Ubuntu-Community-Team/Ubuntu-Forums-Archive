---
title: "Ubuntu 6.10 Edgy Efy Beta DVD problem"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-01
The DVD RW used to install Edgy Beta does show up, but I can't mount any CDs or DVDs in it.  I did a cat /etc/fstab, determined /dev/hdc /media/cdrom0 udf iso9660 user noauto 0 0 was the relevant device and then issued a sudo mount /dev/hdc but still could not read any disc in the drive (same system running Windows all discs work fine and they are not copy protected).  The GNOME mounter works for USB and Floppy disks, but not for the DVD.  Do you know how to fix this?

Thank you!

---

