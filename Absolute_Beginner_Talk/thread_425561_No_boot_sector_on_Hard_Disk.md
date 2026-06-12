---
title: "No boot sector on Hard Disk"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by bgissal on 2007-04-27
I bought a used Dell C400 and a new hard drive. I installed the hard drive and inserted the CD-RW I burned from the Ubuntu website. The CD is feisty fawn.

Before the disk boots, it says, "No boot sector on disk"..."no bootable devices -strike F1 to retry boot..."

Any suggestions will be helpful.

---

### Post by taurus on 2007-04-27
Did you go into the BIOS and have the CD-ROM as the first boot device in the boot order?  Your machine is trying to boot from the harddriv and of course ,it fails since there is nothing on the harddrive right now.

---

### Post by NilsE on 2007-04-27
If it is a new hard drive it will have to be formated before it can be used. Do that from the liveCD when you install.

As far as booting the LiveCD I assume 1) You created the CD using the burn ISO to CD option and 2) that you selected the boot option in the BIOS (either making the CD the primary boot or at least temporary boot) to boot from the CD.

---

