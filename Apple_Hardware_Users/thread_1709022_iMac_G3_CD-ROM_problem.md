---
title: "iMac G3 CD-ROM problem"
date: 2011-03-17
forum: Apple Hardware Users
---

### Post by Rustman80 on 2011-03-17
Ubuntu doesn't seem to register the CD-ROM correctly.  I put media in the CD-ROM and it doesn't recognize it.  Clicking on the CD-ROM under Computer does nothing.  Under disc management the CD-ROM device shows "No media detected".  In terminal I can manually mount the CD-ROM, read from it, and eject it with command line... in the desktop it shows up as a mounted device separate from the CD-ROM.  Great... I can use command line to get it to read the CD I put in.  I'd be fine with that, but these computers aren't for me... I'm giving them to people who probably have no idea what a command line is, much less how to use one.  Any ideas on how I can get it to register the CD correctly under desktop?

---

### Post by Rustman80 on 2011-03-17
One step closer to solving the problem.  For whatever reason, it is associating the CD-ROM with /dev/hdb instead of /dev/cdrom

Must change this....

---

### Post by Rustman80 on 2011-03-18
No ideas?  Will just forcing it into my fstab fix the issue?  or will I end up with 2 cd-rom devices under the desktop, one usable and the other not?

---

