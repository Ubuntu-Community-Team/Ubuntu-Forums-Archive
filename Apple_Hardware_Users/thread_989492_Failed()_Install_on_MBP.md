---
title: "Failed(?) Install on MBP"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by VSMIT on 2008-11-21
I attempted to dual boot Ubuntu with OSX via the instructions found on the help wiki, the rEFIt/Boot Camp method, and on restart after the installation, Ubuntu would not boot.  At the restart, I tried booting Ubuntu from the HDD partition, but all I got was a blank screen with a command line cursor flashing up in the top left corner.  I've installed Ubuntu on a desktop PC before and experienced no problems.  Does anyone know what's wrong?

Thanks.

---

### Post by JairunCaloth on 2008-11-21
I have experienced the same thing several times before. I'm not quite sure what causes it, but I've found that it will usually come up after a reboot (sometimes several).

---

### Post by hyperboloid on 2008-11-22
Have you checked the FAQ's?

There are lots of posts about the bug in the Ubuntu installer that wipes out the MBR when installing Ubuntu on Mac intel. See 
[http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677") for a workaround.

Perhaps that is your problem?

---

### Post by VSMIT on 2008-11-22
Yep, that was the issue.  Refreshed the partitions and it worked like a charm.  Thanks for the help.

---

