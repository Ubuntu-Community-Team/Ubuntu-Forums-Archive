---
title: "[SOLVED] how do i stop the automatic hard disk check?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by mactece on 2007-09-05
Every 38 boots my system runs a hard disk check to look for errors. Not a problem but sometimes when I'm short of time I just need to switch on the pc for one task and then logout and then have to wait for this check which I don't have time for. Rather than pulling out what's left of my hair is there a way to reschedule or break out of this routine? Can I set a prompt to ask if it can be run?

Many thanks

David

---

### Post by BlackMeTaL on 2007-09-05
Bonager: The Boot Scan Manager:
[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

---

### Post by mactece on 2007-09-05
Thanks. Looks like it'll do the job.

David

---

### Post by ajgreeny on 2007-09-05
Or if you want to learn a bit more about using the terminal have a look at **tune2fs.**  Type **man tune2fs** in a terminal to see the manual for the utility.  You can set a different time interval by using this if you want, either in days weeks or months, or after a larger number of boots.  Mine is set for 80 boots which is about every two months according to the way I use my computer.

---

### Post by n3tfury on 2007-09-05
> **mactece said:**
> Every 38 boots my system runs a hard disk check to look for errors. Not a problem but sometimes when I'm short of time I just need to switch on the pc for one task and then logout and then have to wait for this check which I don't have time for. Rather than pulling out what's left of my hair is there a way to reschedule or break out of this routine? Can I set a prompt to ask if it can be run?

Many thanks

David

turning on pc's for one task?  just leave it on then.

---

