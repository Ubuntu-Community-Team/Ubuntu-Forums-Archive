---
title: "npviewer maxing CPU"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-16
when i am on Pandora, after a while npviewer with max out about 200% of my cpu(both cores near 100%), anyone also having this issue and is there any way to fix it?  I have running ubuntu 7.10 64-bit.

---

### Post by mkarnicki on 2008-04-06
Bump! I have the same problem. Npviewer utilizes both cores up to 100% and the fan even kicks in. How can I "nice" npviewer? I don't want my laptop heat up because of some youtube clips. Thanks.

---

### Post by ELMIT on 2008-04-20
Youtube you end watching after a while, but Yahoo email will pop up the next ads within soon again, ... 
I also use AMD64.
Any cure? or will be 8.04 in three days be the solution?

---

### Post by yaknowwat on 2008-04-20
This is possibly an issue with Adobe's flash as npviewer is from nsplugginwrapper normally used to wrap flash for 64-bit linux system setups

---

### Post by tchalvakspam on 2008-06-25
I've had a similar cpu overuse issue while running a high-flash-intensive web-app (pandora.com) in opera, could potentially have to do with some part of that site's code on its own, but on the other hand might be the npviewer needlessly overusing cpu when wrapping the flash in opera, hard to say.

---

### Post by mkarnicki on 2008-06-26
I played around with powernowd and it helped somewhat. You can use:

sudo powernowd -m 2

To switch your AMD64 to passive mode, by default it's in -m 1 aggressive mode. The CPU should behave little better.

note: you will be prompted for admin password for security reasons

---

