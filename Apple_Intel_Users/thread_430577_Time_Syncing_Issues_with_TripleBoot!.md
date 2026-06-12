---
title: "*Time Syncing Issues with TripleBoot!*"
date: 2007-05-02
forum: Apple Intel Users
---

### Post by Chrisj303 on 2007-05-02
Hi, This is a problem that i have experianced ever since i first setup my TripleBoot macbook (OSX/UBUNTU/XP). I am having problems keeping the TIME on all three OS' consistent. I have tried booting into each OS' and correcting it, one after another. But it only takes one cold reboot before they are all out again.
The time delay is normally 1,2 or 3 hours - the minutes i don't think have ever been an issue.

This is really starting to annoy me - it looks dumb and i can't tell the time from my desktop properly. But the real problem is when i have written to my ubuntu partition from another OS' , when i next boot ubuntu it sometimes comes up with the message :

"/dev/sda3 LAST RIGHT TIME IS IN THE FUTURE CHECK FORCED"

Then it runs fsck (i think), it will always return saying that it has fixed the problem but needs to restart.

Is there some way i can set the time of all 3 OS at the same time(!) ?. 
I can't be the only triplebooter experiencing this (can i ?!)..


Thanks in advance for any replys,

chrisj303

---

### Post by Azathoth_ on 2007-05-02
It's normal. All we have this problem, because Windows and Ubuntu use a different syn than Mac OS X. Ubuntu and Windows use GMT and Mac OS X uses CEST, which is 2 hours more

---

### Post by ronocdh on 2007-05-02
> **Azathoth_ said:**
> It's normal. All we have this problem, because Windows and Ubuntu use a different syn than Mac OS X. Ubuntu and Windows use GMT and Mac OS X uses CEST, which is 2 hours more
Yup. I hates it, but it gets me too. Time autosyncing in OS X isn't what I had hoped for, either. Ubuntu is more often correct.

---

### Post by Gen2ly on 2007-05-02
I'm using gentoo at the time but it may be similiar.  See if you have a "/etc/conf.d/clock" file and if you do that time is set to UTC.  Also some linux's have a file that calculates natural drift of the clock.  See if you have "/etc/adjtime".  If you do it's safe to remove it as it will be recalculated.

---

### Post by Azathoth_ on 2007-05-05
I hope (only hope) that in Leopard this issue may be solutionated.
I only have 1 subject in my career and i have arrived later because this problem :P

---

### Post by Chrisj303 on 2007-05-05
> **Dirk.R.Gently said:**
> I'm using gentoo at the time but it may be similiar.  See if you have a "/etc/conf.d/clock" file and if you do that time is set to UTC.  Also some linux's have a file that calculates natural drift of the clock.  See if you have "/etc/adjtime".  If you do it's safe to remove it as it will be recalculated.

No, i don't have /etc/conf.d/clock. The nearest i have is /etc/cron.d ?. I do however have /etc/adjtime - i will delete it and see what happens (!).

cheers,
chrisj303

---

