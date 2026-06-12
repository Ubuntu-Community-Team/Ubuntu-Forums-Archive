---
title: "Question about accesing information from dual booting"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by JoePorter on 2007-08-18
I plan on dual booting using this method
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


However I have 1 question.

Say I was to download a video or save favorites on a web browser and I was currently on either Vista or Ubuntu.

If I switched to the other OS, What would happen?  Would I have that video saved onboth OS's and the favorite say in Firefox both on Vista and ubuntu?


Here's the computer i'm purchasing next week =o
[http://pc.ncix.com/pcbuilder/index.php?action=getprice&id=2611081&platformid=1000](http://pc.ncix.com/pcbuilder/index.php?action=getprice&id=2611081&platformid=1000)

---

### Post by Fonon on 2007-08-18
No, the file would stay on the OS you downloaded would stay on that OS.  However, I believe you can access the file you downloaded from the other OS through partitions.

The Favorites are not automatically transferred.

---

### Post by kellemes on 2007-08-18
You want to have a seperate partition for sharing files.. So when you download stuff and want it to be available from both OS's, simply put it on this partition.. You can have access from both OS's, no problem.

Specific packages like Firefox can also share data (like favorites) by sharing profiles (basicaly the profilefolders on disk).
So.. from GNU/Linux instruct Firefox to put it's profiledata on the "shareparition" and from Windows instruct Firefox to use this profilefolder (or the other way around).

---

