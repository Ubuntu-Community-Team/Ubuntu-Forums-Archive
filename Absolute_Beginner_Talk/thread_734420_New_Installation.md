---
title: "New Installation"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by regdabs on 2008-03-24
I am thinking about installing Ubuntu on my computer, at the present time I have 4 partitions on my hard drive  1.  XP  2. Freespire  3-4. data files.  I want to install Ubuntu on the drive over Freespire. Will this work, will it completely overwrite the Freespire drive with Ubuntu and will I have a problem with the boot loader. Hope I can do this with no problems.

---

### Post by Sam Lars on 2008-03-24
You should get the option of where you want to install it, and you should be able to choose the Freespire partition.
What are you using for your bootloader now?  I think Ubuntu would install its own as the primary and add options for everything else there (Windows for you), but I'm not sure on that.

---

### Post by Hospadar on 2008-03-24
It will totally overwrite freespire (if you install it into those partitions during installation) make sure you select the "manual partitioner" during installation.

The installer should install a new version of grub which should boot ubuntu and windows just fine.

---

### Post by regdabs on 2008-03-24
Thanks for the info, that's what I wanted to know if it would install a new version of grub and get rid of the freespire and let me dual boot with XP, I have had a few problems with Freespire and wanted to try something new.

---

### Post by Sef on 2008-03-24
> I think Ubuntu would install its own as the primary and add options for everything else there (Windows for you), but I'm not sure on that.

Windows has to be on the first partition.

---

