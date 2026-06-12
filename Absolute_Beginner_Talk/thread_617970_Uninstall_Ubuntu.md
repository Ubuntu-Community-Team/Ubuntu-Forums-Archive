---
title: "Uninstall Ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by alienduckie on 2007-11-19
I'm done with Ubuntu.
I've tried tweaking it, fixing it and it's just not for me.
How do I just get rid of it from my computer like I never installed it?

---

### Post by LaRoza on 2007-11-19
Reformat the partition. If you are dual booting, you will have to restore the MBR for Windows, use the Super Grub Disk for that.

You can use the WIndows "Disk Management" to delete the partition and expand the Windows partition to the freed space. At this point, Windows will not be able to boot. 

You can install the Windows Boot Loader with the Super Grub Disk before doing that, to ensure WIndows will boot. (This will make Ubuntu unbootable) Then you can delete the partition.

---

### Post by DoctorMO on 2007-11-21
Oh and don't forget to backup any files you have created on your ubuntu install.

---

