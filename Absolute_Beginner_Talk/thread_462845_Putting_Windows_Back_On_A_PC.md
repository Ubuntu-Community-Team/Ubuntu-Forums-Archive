---
title: "Putting Windows Back On A PC"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by SolidusRegime on 2007-06-03
Okay, well I have been using Linux Ubuntu for a while now. I have just gotten a new job, and been forced to use Windows on my Personal Laptop. I tried booting from the Windows XP disk, and everything loaded, when it came to the screen where I install it, it said there are no HDD.

Is there a reason why my HDD is not recognized by Windows XP after using Ubuntu on my Laptop? My entire 60GB HDD is used for Ubuntu, and I do not wish to dual boot. I just want to somehow get my entire HDD formatted so I can run XP on it again.

---

### Post by jd65pl on 2007-06-03
Try formatting a partition on your hard disk to ntfs, that might help it out. You might need [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") if you are keeping ubuntu after installing windows.

---

### Post by louieb on 2007-06-03
[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by hellmet on 2007-06-03
Ubuntu has previously killed my partition table . I think its a similar case.
Try searching in this forum for solutions on that.

---

### Post by Feba on 2007-06-03
Is there a reason you need to use XP? You might find that there's a solution to do what you need to on linux.

---

### Post by SolidusRegime on 2007-06-03
I actually figured this one out myself. A mate of mine had to do the same thing when he got his job at Blizzard, he told me how to do it. What you do is go into your BIOS setup and disable SATA Native. Then just boot from the CD and it works fine.

---

