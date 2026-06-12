---
title: "OpenOffice.org Infinite AutoRecovery Loop"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2007-08-08
Hi, I had some slideshows open with Impress, and I opened up Writer and all my files crashed.  OpenOffice.org restarted and tried to recover them, but it keeps crashing upon recovery.  And now I can only click ok to recover.  There is an infinite loop of crashing.  How do I bypass this?

---

### Post by Al3xK3aton on 2007-08-08
Just buy MS Office, it works better anyway, the thing is you'll also need to buy Windows to use it. It's really your own fault for using freeware, which is notoriously unreliable.

---

### Post by ThrobbingBrain66 on 2007-08-08
> **leetcharmer said:**
> Hi, I had some slideshows open with Impress, and I opened up Writer and all my files crashed.  OpenOffice.org restarted and tried to recover them, but it keeps crashing upon recovery.  And now I can only click ok to recover.  There is an infinite loop of crashing.  How do I bypass this?

Try opening Writer in a terminal to see if it spits out any errors:

```
ooffice -writer
```

and post them here.

---

### Post by ThrobbingBrain66 on 2007-08-08
> **Al3xK3aton said:**
> Just buy MS Office, it works better anyway, the thing is you'll also need to buy Windows to use it. It's really your own fault for using freeware, which is notoriously unreliable.
The OP was asking for help, not a troll.

---

### Post by Hagar Delest on 2007-08-09
Remove the Ubuntu version of OOo and install the official version. See here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by leetcharmer on 2007-08-11
> **Hagar de l'Est said:**
> Remove the Ubuntu version of OOo and install the official version. See here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

lawl, that seems to be a common solution to all my OOo problems among multiple computers.  Hope Gusty proves to solve a lot of this out of box :D

---

### Post by leetcharmer on 2007-08-11
> johnny@jBox:~$ ooffice 

** (process:7286): WARNING **: Unknown error forking main binary / abnormal early exit ...
That's what I get currently before installing a new version of OOo

---

### Post by Hagar Delest on 2007-08-11
A very very common error message but it seems it can comes from multiple reasons. I've not managed to find a pattern. Can be the graphic driver, corrupted OOo user profile, the Ubuntu version (vs. official one), ...

---

