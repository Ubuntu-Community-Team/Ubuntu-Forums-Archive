---
title: "Problems with Headers and Wireless card"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by teruokun on 2007-02-04
Hi,

I just installed Ubuntu on my Dell Inspiron 6000 a few days ago.  I've been trying since then to get the wireless network card working with no effect.

I've even been through almost all of this thread with no luck:
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

I think the problem might have to do with my headers installation, but I've tried re-installing it and it hasn't changed anything.  The big problem is that when I run the "Make" command for iee80211-1.2.16, I get this message

Checking in /lib/modules/2.6.17-10-generic for ieee80211 components...
make -C /lib/modules/2.6.17-10-generic/build M=/home/jeff/ieee80211-1.2.16 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-generic/build'
make: *** [modules] Error 2

Yet, when I look for the 'modules' file in /usr/src/2.6.17-10-generic/   there is broken link to the modules file which is supposed to exist in /usr/src/2.6.17-10/

I would imagine this is actually the file I need but I'm wondering:
1.  Is it the file I need?
2.  If it is, where can I get it?

Any help would be appreciated 
thanks!

---

### Post by teruokun on 2007-02-04
Oh, and I'm using edgy eft.  

Would it be easier if I switched to Dapper drake or is there a possibility I'll still have these kinds of problems?

---

### Post by Tinwood on 2007-03-12
Funnily enough I have exactly the same problem.  Did you manage to solve it, and if so, how.  I too am on Edgy and it was an upgrade from Dapper.  My 'brand new install' amd64 Edgy box doesn't have this problem.

---

