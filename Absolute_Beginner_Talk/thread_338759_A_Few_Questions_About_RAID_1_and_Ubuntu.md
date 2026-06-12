---
title: "A Few Questions About RAID 1 and Ubuntu"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2007-01-14
Hi,
I was wondering If Ubuntu Edgy is compatible with Raid 1, and if it isn't, is it possible to just utilize one of the hard drives?

Also, assuming I already have a computer with 2 HDDs in RAID 1 and a Ubuntu 6.10 Live/Install CD, how would I go about installing it on the RAID 1 configuration (or just a single hard drive it if isn't compatible)

Any links to helpful guides would be appreciated.

Also, include procedures with GRUB if applicable, please.

Thanks,
Navid

---

### Post by Marsolin on 2007-01-15
How is your RAID 1 array set up now? If it is done through an Option ROM before booting into an OS then Ubuntu doesn't even need to be aware of it.  It will just see the array as one drive and the mirroring will happen independently.

If your motherboard doesn't have any special RAID capabilities then you can create a RAID array during Ubuntu install. It's done in the partitioning step.

To install Ubuntu all you need to do is boot to the LiveCD and select the install link from the desktop.

---

