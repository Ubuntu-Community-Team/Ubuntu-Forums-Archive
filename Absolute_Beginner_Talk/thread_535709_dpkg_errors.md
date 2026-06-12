---
title: "dpkg errors?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Jjjakal on 2007-08-26
Im have a bit of trouble with my newly installed Ubuntu.  Im trying to get some games and such on it, for starters, and see what else I could get.

Attempt 1)
Tried running Add/Remove.

What happened:
It asked me to update the list of programs, I clicked yes, and it greyed out like it was working, and did nothing.  I couldnt even close it.  Had to restart. 

Attempt 2)
Updating with the update manager.

What happened:
It asked me to update, I clicked yes, and it greyed out like it was working, and did nothing.  I couldnt even close it.  Had to restart. After restarting, I tried again, same thing, but the number of updates went from 166 like it was the first try, to 46.

Attempt 3)
Tried running Synaptic Package Manager.

What happened:
```
E:dpkg was inturrupted, you must manually run 'dpkg --configure -a' to correct this problem.
E:_cache->open() failed, please report.
```

Attempt 4)
Tried using the Terminal and sudo apt-get update and sudo apt-get upgrade to make it work.

What happened:
```
E:dpkg was inturrupted, you must manually run 'dpkg --configure -a' to correct this problem.
```

Also, this may or may not be related, but when trying some other commands, such as cp /etc/x11/xorg.cong /etc/x11/xorg.conf.backup, to try to fix my screen resolution, It says "Permission Denied", and on a couple of them, "Must have Superuser privledges" or something along those lines.


How can I get Add/Remove, Synaptic Package Manager, or anything else to work?

---

### Post by rkrug on 2007-08-26
This may sound dumb, but have you actually tried running "dpkg --configure -a"?

---

### Post by Jjjakal on 2007-08-26
Oh yeah, I really forgot to say that.  The error when I run that is:
```
dpkg: requested operation requires superuser privelege.
```

Same error on --purge

---

### Post by bump_ on 2007-08-26
just add "sudo" before it

"sudo dpkg --configure -a"

---

### Post by beaversqueezer on 2007-08-27
Thank you,bump.I'm a newb to Ubuntu and Linux and did'nt know what happened either but your reply fixed it.Thanks again,beaversqueezer

---

