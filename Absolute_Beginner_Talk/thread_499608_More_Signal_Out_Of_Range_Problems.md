---
title: "More Signal Out Of Range Problems"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by jimcrockett on 2007-07-12
I loaded 7.04 yesterday from the live CD to a new WDC 80G HD.  My XP is on the master original Maxtor 40G HD in my HP 540n.  In both the live CD startup and the original boot after install, I get the "signal out of range" blinking screen for a few minutes.  With the live CD, Ubuntu eventually loads, but with the installation boot, I get the "cannot access tty" failure screen.

I've read every thread on the web it seems like and it seems I need to set my monitor refresh rates since Unbuntu is probably setting them too high for my monitor - Princeton LCD-1700.  So I press ctrl+alt+F1 at the "signal out of range screen", the failure screen, and every where else, but I can't edit or get into the monitor file.  I tried sudo  dpkg-reconfigure xserver-xorg, but nothing gets me to a file I can edit.  

Since it doesn't work from the live CD because it won't change the real installation files, how do I get into the new HD where Ubuntu was installed to specify my monitor parameters?

---

### Post by jimrz on 2007-07-12
"cannot access tty"

take a look at [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1") thread and see if you can boot the live cd this way. it may not be a monitor issue at all.

---

### Post by jimcrockett on 2007-07-13
Sorry for the delay - with dial-up Internet, everything is slow.

I did F6 at the menu with the live CD, typed in live boot=break, but it didn't go to the command line - just went to black screen with flashing "Source out of range", and after about 3 minutes the live CD boots into the Ununtu screen.

Somehow, I need to get to a command line and modify the screen refresh rates.  I think I have two problems - once I get the refresh rate right, I can go after the "Can't access tty" problem.

Thanks - I think I'll post a new question on accessing the command line.

---

