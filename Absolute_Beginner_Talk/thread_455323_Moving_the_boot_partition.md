---
title: "Moving the boot partition"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-05-26
I installed Ubuntu on an external hard drive, but now I get a GRUB 18 error.  It is my understanding that this means the BIOS cannot read far enough into the hard drive to get to the boot partition.  I'd rather not do anything with the BIOS, so I think I need to move the boot partition to the front of the hard drive.  I really have no idea how to do this, so could anyone help me out?

Thanks!

---

### Post by rillip on 2007-05-26
If it's installed in the boot section of the disk, this is something more like hardware support, not sure how you would do it and it would probably differ on the drive architecture.

But if you just have grub installed in /boot, it'll be a simple matter to back it up, delete the partition, then put it on a partition with a lower number, i.e. sdb1.  I'm not really sure that will address the issue, as I'm not that familiar with Grub's inner workings, but maybe it'll give you ap lace to start.

---

