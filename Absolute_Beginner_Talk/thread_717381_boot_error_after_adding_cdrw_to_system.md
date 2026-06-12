---
title: "boot error after adding cdrw to system"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by strBean on 2008-03-07
hey

First foray into Linux: Ubuntu 6.06.  Pretty friendly stuff.  It came set up on a box from a cool nonprofit in Portland called FreeGeek.  Already had a CDROM.  I dropped in a used CDRW and started it and it hung up on mounting root file for a while, then said ok, the hung up bad on loading hardware drivers, then said FAILED and finished booting, and then the system couldn't find any CD drives at all, giving the error message:
mount: can't find whatever/whatever in wherever/and so forth
and when I unhook the added drive and boot again it boots like a cup of coffee and it can find the CDROM drive just fine.

I find nothing in Help so far about adding a drive like this, so I wonder if it's just simple and automatic and this drive is just no good, or is there something I'm supposed to do to get the system to find the new drive next time it boots?

Hey, this forum has very sophisticated features.  Very nice work.

---

### Post by spiderbatdad on 2008-03-07
Just a guess..it sounds like the linux  drivers aren't suitable for this cdrw. You could browse the synaptic package manager in 6.06 and look for packages like "linux-restricted-modules-generic..." I'm not sure what's in the Dapper repos. But downloading additional modules may solve your problem.

---

### Post by plucky on 2008-03-07
strBean,


Did you setup the **Master/slave** jumpers for both **CD** drives?
Are the CD drives on a separate IDE channel?
Is one drive setup for cable select?
Can you see both drives in the **BIOS** display when you boot?

I always forget the jumpers on the back of the drives.

Good luck

---

