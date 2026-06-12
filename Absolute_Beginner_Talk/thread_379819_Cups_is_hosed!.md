---
title: "Cups is hosed!"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2007-03-08
I was trying to share a printer off of my 6.10 desktop to a XP computer, and somewhere along the way I have completely messed up Cups where I can't even print from my desktop anymore.  

Can cups be reinstalled?

---

### Post by OMRebel on 2007-03-08
To give a bit more information, when I try to print to a printer that was working perfectly before, I get:
Paused: job-hold-until-specified
That is showing in the State.  I've restarted Cups and the print services, but no avail.  I'll try to resume the print job, but it goes back to the Paused status.  

What do I do?

---

### Post by OMRebel on 2007-03-08
Looking at the log file in cups, it gives me:

E [08/Mar/2007:21:35:20 -0600] PID 8099 (/usr/lib/cups/backend/z600) stopped with status 1!
E [08/Mar/2007:21:35:20 -0600] [Job 180] No %%BoundingBox: comment in header!
E [08/Mar/2007:21:35:20 -0600] [Job 180] Unable to open printer port "/dev/usblp0": Permission denied

---

### Post by OMRebel on 2007-03-08
After beating my head against the wall, I added cupsys to the plugdev group, and that actually got it working.

---

### Post by silentb on 2007-03-09
Nah, look here:

[http://ubuntuforums.org/showthread.php?p=2270082#post2270082](http://ubuntuforums.org/showthread.php?p=2270082#post2270082)

It's not your fault. It's a backported package's fault (libgphoto2).

---

### Post by OMRebel on 2007-03-09
Cool.  Thanks for posting that link.  I'll go through and make sure those files are set right.

---

