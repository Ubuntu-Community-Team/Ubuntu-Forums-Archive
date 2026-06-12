---
title: "2nd HDD suddenly disappeared"
date: 2012-09-05
forum: Apple Hardware Users
---

### Post by mareoraft on 2012-09-05
I recently installed a 2nd HDD in my optical drive space using an optibay imitator.  Basically, there is a PATA to SATA converter so that I have an HDD instead of a disk drive.  On my regular SDD I put MAC OSX, and on the HDD I put Ubuntu.  I have a late 2006 MacBook.

Everything worked great except for one minor glitch.  When I would restart my mac, the computer wouldn't see the Ubuntu HDD.  I believe it is because the HDD wasn't spinning in time for the kernel to see it.  Anyways, when I would turn my computer off completely, and then turn it on, everything worked perfect.

Today, for no apparent reason, when I turn on my Mac (NOT restart) the 2nd HDD is missing.  Any Ideas?

---

### Post by mareoraft on 2012-09-06
It seems to have begun working, although now when I boot Ubuntu it gets stuck on the part where it says it is starting the CUPS server.  How can I fix this?

---

### Post by einonm on 2012-09-23
I would hazard a guess that there isn't enough power being given to the disk to spin up. 

If the disk doesn't have a separate power supply, and is using the mac for power, you may not be able to solve the issue.

The Ubuntu startup stalling may be a related issue - there's not enough power to go round as devices are started up, causing the OS to hang / freeze.

---

