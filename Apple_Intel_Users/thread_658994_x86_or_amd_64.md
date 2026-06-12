---
title: "x86 or amd_64?"
date: 2008-01-05
forum: Apple Intel Users
---

### Post by Aifel on 2008-01-05
Just wondering; what architecture should I go for? I already have a Ubuntu i386 livecd, and was wondering if amd_64 was a better idea for a Macbook (2006).

---

### Post by Sef on 2008-01-05
If you do heavy gaming, or movie editing, or run more than 4 GB ram, then 64-bit will definately be better.  If not, then it really won't make much of a difference.

---

### Post by fabietto0102 on 2008-01-06
I have the amd64 Ubuntu 7.10 installed and this is causing minor problem in comparison to i386: the flash/java items in some webpages do not display correctly and totem movie player is behaving a bit weird. On the other side, cd ripping and encoding is really fast. We all know these minor details will fix within few months from the Ubuntu experts via updates, but still, my suggestion is: unless you are a really expert user, stick with i386 till further notice: you have more support, more choice on apps, and a more stable OS. 

For myself, I will playing around a bit with amd64 but will revert back to i386 at the next occasion.

---

### Post by regomodo on 2008-01-06
flash/java issues are not only applicable to Ubuntu. Debian testing has flash issues where in firefox it'll suddenly stop working and a restart of firefox will fix it. Java is a pain to install and i just cannot be arsed to sort it out.

Compared to i386 amd64 is an inconvenience for those 2 applications but other than it is fine. CD ripping, video encoding etc work very well in 64bit land even if some app's don't use multi-core cpu's that effectively.

---

### Post by handy on 2008-01-06
I installed the 64bit Ubuntu 7.10 alternate install on my current iMac yesterday, & it was probably the smoothest install I've ever had.

You need to [***_rEFIt_***]("http://refit.sourceforge.net/") though.

Also, if you use 64bit, check that ***ia32-libs*** is installed, it may smooth out things for 32bit software, it certainly does for CrossOver.

---

### Post by macaholic on 2008-01-06
64-bit is noticeably faster, and in gutsy flash is really easy to deal with, java is a little harder, but doable. Also if there are any 32-bit only apps, which there are very dew of, you can usually find a way to install them with minimal errors, jsut search around.

---

### Post by cyberdork33 on 2008-01-07
the 32bit on 64bit OS works very well on gutsy... there is almost no need to do any special configuring. I have been running 64bit for awhile on my iMac, and have had no issues with flash or java, just have to install them, and it gets the required 32-bit libraries.

---

### Post by handy on 2008-01-07
> **cyberdork33 said:**
> the 32bit on 64bit OS works very well on gutsy... there is almost no need to do any special configuring. I have been running 64bit for awhile on my iMac, and have had no issues with flash or java, just have to install them, and it gets the required 32-bit libraries.

I found that the CrossOver nightly builds don't install the ia32-libs, but the 6.2 commercial version does. (The hard way) :-)

I know nothing about the variety of 32 bit libraries that may be required by different software to run on 64 bit Linux.  Though it seems like it is all but transparent to the user at this point, in Ubuntu at least.  Which is nice.

---

### Post by Victormd on 2008-01-07
I've tried both and must say that even though 64-bit requires a bit of work and poking around to get it up and running, it's worth it in the end. However, if you just want a smooth and worry free install, go with the x86.

---

### Post by cyberdork33 on 2008-01-08
> **handy said:**
> I found that the CrossOver nightly builds don't install the ia32-libs, but the 6.2 commercial version does. (The hard way) :-)

I know nothing about the variety of 32 bit libraries that may be required by different software to run on 64 bit Linux.  Though it seems like it is all but transparent to the user at this point, in Ubuntu at least.  Which is nice.Ok, I will reiterate... installing software from the repos doesn't require tinkering.

---

### Post by handy on 2008-01-08
> **cyberdork33 said:**
> Ok, I will reiterate... installing software from the repos doesn't require tinkering.

We don't all just use the repo's! :lolflag:

---

### Post by cyberdork33 on 2008-01-09
> **handy said:**
> We don't all just use the repo's! :lolflag:
Yes, I stand corrected.:)

---

