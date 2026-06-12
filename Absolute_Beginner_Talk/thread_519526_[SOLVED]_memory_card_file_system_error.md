---
title: "[SOLVED] memory card file system error"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-08-07
Hi

I have a major problem with a memory card on my system.

One of the directories on an SD card got corrupted, I managed to copy everthing else that was important off the drive to a folder on my desktop, unfortunately I had forgotton how to format the drive so I right-clicked and in the file-system text box entered vfat-16.  Now when I insert the card I get the error message that fat-16 is an incompatible file system.

I subsequently have formatted the card correctly using 

mkdosfs -I /dev/sdd

However, the same error message appears when I insert the drive, I assume that I have set some incorrect label with my incorrect entry in the file-system text box, how can I reset this label I assume that Ubuntu is picking this up from the SD card UUID but where does it keep these settings.

Obviously I cannot correct my original mistake in the same way as I cannot mount the card.

Thanks

Ian

---

### Post by svega85 on 2007-08-07
hat you tried a blank file-system textbox?

---

### Post by ushills on 2007-08-08
Hi

Thanks for the reply, I cannot get to the text box as I cannot mount the card to the desktop, however, I solved the problem.

By editing the .gconf settings I was able to reset the filesystem type to vfat, all is good now

---

