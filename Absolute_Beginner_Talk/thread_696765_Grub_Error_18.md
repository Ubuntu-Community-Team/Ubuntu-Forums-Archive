---
title: "Grub Error 18"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by five_tools on 2008-02-14
I just installed Kubuntu.  I reset, for the changes to take effect.  Grub gave me an Error 18.  I heard it means the BIOS thinks the disk is too large.  I read another thread that had a few solutions, like creating a small partition or changing the BIOS settings.  But, I don't know how to do those things.  Can somebody tell me the best solution, and walk me through it a little bit?

---

### Post by dstew on 2008-02-14
This error means that your BIOS cannot access cylinders above I think 1024, and therefore grub could not load its stage2, because it is in a partition that exceeds that limit. The way to get around this is to reinstall Ubuntu, and make a small (50 Mb) partition at the front of the drive, formatted ext3, with the mount point /boot. Then, make the other root and swap partitions as usual. When Ubuntu installs, it will put the grub files and the kernel images grub needs to access into the /boot partition, and set up everything to boot properly.

Note it is not enough to hope that the /boot directory of the root partition is at the "front" of the partition, within reach of the BIOS. The *_entire_* partition containing the grub and kernel files must be within the limit. Depending on drive geometry, the largest partition that can be reached by these BIOSes is about 8 Gb. But the /boot partition only needs to be 50 Mb, because that is enough for the grub and kernel files.

---

### Post by five_tools on 2008-02-14
Thanks.  I forgot to mention I have a dual-boot w/ XP.  I think XP is the first partition, since it was installed first.

I saw some people were having luck by changing their bios HD setting from "LGA" to "normal".  I'm completely new to changing bios settings.  I found out you're supposed to hold F1 or F2 to bring up the bios settings, but all I get is the GRUB error when I startup.  Should I explore this path a little more?

---

### Post by almaddin on 2008-02-14
> **five_tools said:**
> Thanks.  I forgot to mention I have a dual-boot w/ XP.  I think XP is the first partition, since it was installed first.

I saw some people were having luck by changing their bios HD setting from "LGA" to "normal".  I'm completely new to changing bios settings.  I found out you're supposed to hold F1 or F2 to bring up the bios settings, but all I get is the GRUB error when I startup.  Should I explore this path a little more?

no just try what dstew says. since upgrading your BIOS most certainly isn't an option if this even is the first time you ever touched your BIOS.

---

### Post by five_tools on 2008-02-14
I thought dstew was saying the /boot partition had to be at the **front** of the drive.  Since the XP partition is at the front of the drive, I thought I couldn't do it.  So, do I just have to put the /boot partition at the front of partition #2 for it to work?

---

### Post by five_tools on 2008-02-14
OR... Can I put the /boot partition in front of XP's partition?  If so, how would I do that?

---

### Post by dstew on 2008-02-14
Yes, you have to put the /boot partition in front of the XP partition. I assume you are going to dual-boot. Once you have grub set up, it won't matter that XP is not the first partition.

You will need to shrink the XP partition from the front in order to make room for the /boot partition. The installation partitioner will allow you to do this, I think. But, make sure you back up your important files, and be prepared to re-install XP if something goes wrong.

---

