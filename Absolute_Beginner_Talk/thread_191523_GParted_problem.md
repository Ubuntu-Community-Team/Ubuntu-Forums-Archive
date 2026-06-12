---
title: "GParted problem"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by fhqwhgads on 2006-06-07
Sorry for asking here, it looks like the GParted forum doesn't get much traffic. I figure this may be user error and somebody here can tell me what I did wrong or how to fix it. Okay, here's the layout of the drive before using GParted.

/dev/hda1 - 10.00 GB - NTFS (WINXP)
/dev/hda2 - 5.00 GB - EXT3 (ROOT)
/dev/hda3 - 5.00 GB - EXT3 (EMPTY)
/dev/hda4 - 73.16 GB - Extended (MOUNT POINT)
     /dev/hda5 - 2.00 GB - (SWAP)
     /dev/hda6 - 71.16 GB - EXT3 (HOME)

Everything was cool, but the ROOT partition was quickly running low on space. It was up to 3.31GB of space used. I used GParted to delete the empty partition (/dev/hda3) and extend the root partition (/dev/hda2) to fill the space I created. Now the root partition is 10GB, which is what I wanted, but there's a problem.

Ubuntu's system disk tool shows the data on the partition as 8.77GB of 10.00GB used. Filelight, on the other hand, shows 3.31GB of 10.00GB used, which should be correct. What is this extra data that Filelight cannot see, but the disk tool and Gparted both see? Is there any way to get this space back?

---

### Post by fhqwhgads on 2006-06-08
Help?

---

