---
title: "Skype Freezes"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by SZorg on 2006-12-23
About 25% of the time when I call/receive a call, Skype will freeze my computer for roughly 30 seconds. It's not a terrible problem so if no one has a solution off-hand, don't worry about it -- but if there's a solution, I'd love it.

---

### Post by carlosfocker on 2007-01-05
What version of skype are you using.  I had a similar problem with the version of skype that only supported oss sound drivers.  From version 1.3.0.50 and up this problem should disappear.

---

### Post by MJN on 2007-01-08
Do you have any mention of ***BUG: soft lockup detected on CPU#0!** *in /var/log/kern.log? If so, this seems to be a common issure for many with Skype (and Ubuntu judging by the number of reports, however this could just be a reflection of its popularity).

As far as I'm aware it's yet to be resolved - noone really knows whether it's a kernel or Skype issue although whichever it's pretty serious given the DOS vulnerability this could be... just phone someone up and there machine crashes!

[http://lkml.org/lkml/2006/10/11/200](http://lkml.org/lkml/2006/10/11/200)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53216)

Mathew

---

