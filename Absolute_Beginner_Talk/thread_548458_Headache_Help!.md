---
title: "Headache Help!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-09-11
I just got Ubuntu working on my machine.  Now I'm having hell getting the dual monitor thing to work.  I've followed just about all the How-To's / helpers out there, and I can not for the life of me get dual screens to work.  I have an ATI card, so if ANYONE out there has a little guidance, please send it my way.  THANKS!

---

### Post by finer recliner on 2007-09-11
best bet: [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)


just keep working on it. do small tweaks one line at a time until you get the desired result.

---

### Post by CowzRule on 2007-09-11
Back some time ago when I was running Ubuntu 6.10 Edgy Eft with a ATI x800 pro agp card I was running 2 crt monitors. I remember it was a real pain to get it to work but I was successful. 
Basically it was a matter of getting xorg.conf set up correctly for the drivers that are being used.
Have a look through the xorg.conf files I've attatched to this post. Since you didn't say what model card or what drivers you're using I've included 2 files.
The file titled "ati-dualmonitors-radeon" was the xorg.conf file I used with the open source Radeon drivers. If you got a fairly new card, and you want to have 3d (for Beryl - Compiz) this will NOT work. You'll get dual monitors but without 3d.
The file titled "ati-dualmonitors-fglrx" was the xorg.conf file I used with the binary FGLRX drivers from the ati/amd web site. With this you'll get 3d, provided you have the drivers installed correctly, but you'll need to use XGL to be able to run Beryl - Compiz.
I edited the files with Open Office so I could highlight the sections that needed to be adjusted so open them with that.

---

