---
title: "Windows bootloader + Erasing Ubuntu"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-26
How do I erase Ubuntu and GRUB bootloader and then add the Windows bootloader? I tried deleting the Ubuntu partition, but the GRUB commandline was still loading, and I couldn't get into Windows. I tried using my boot CD, and I went into the recovery console and typed FIXMBR and FIXBOOT, but after that, whenever I tried booting, it would give some weird lines of text and then say like "insert boot CD and press F1 or press F2 to go to setup menu." I had to resort to reinstalling Ubuntu, and now I have to use GRUB to load into Windows. I just want to have my Windows partition and the Windows bootloader ](*,)

---

### Post by bulldog on 2006-11-26
If you have a windows install disk you should go to the recovery console and type fixboot and/or fixmbr.

This is the only thing you have to do to get your windows boot loader back.

If it's not working just do it again.

To erase Ubuntu just reformat or delete it's partitions.

---

### Post by kbsuperstar on 2006-11-26
K, i'll try it. Thanks

---

### Post by kiyometane on 2006-11-26
fixmbr will remove the grub.

---

