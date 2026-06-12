---
title: "MBP Retina Resolution Problem"
date: 2014-04-17
forum: Apple Hardware Users
---

### Post by rkeatin3 on 2014-04-17
I'm running xubuntu 12.04 on my MBP 10,1, and I'm having trouble setting the default resolution.

I followed [this guide]("https://wiki.ubuntu.com/X/Config/Resolution") to attempt to make a new resolution, but get the following error when I try to add the new resolution I created:

> 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40


I also found that the xrandr scale command works well, but can't figure out how to properly execute it on login. I added the command to run from a terminal in the Session and Startup settings, but for some reason the command does not work the same: instead of scaling the resolution and keeping the panels in place, it scales the resolution so that the whole desktop is scrollable and the bottom panel does not appear. 

Any ideas?

Also, I'm very new to linux, so keep that in mind when suggesting solutions.

---

### Post by QIII on 2014-04-18
*Moved to **Apple Users***

---

