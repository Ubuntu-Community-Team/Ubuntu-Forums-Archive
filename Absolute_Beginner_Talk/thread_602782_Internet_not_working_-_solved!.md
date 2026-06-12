---
title: "Internet not working - solved!"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by el10t on 2007-11-04
Hi all, 

Not sure whether this will be of help to anyone but I thought I'd post it just in case.  I'm a novice so be gentle if I've made any silly mistakes in this :)

I was having big trouble with accessing the internet using Gutsy.  I was able to access my local network over the wireless connection, but no websites could be found, and pinging addresses failed too.  After reading a number of threads on here it appeared this was something to do with IPv6 incompatibility.  I tried all the solutions about adding "alias net-pf-10 off" to my "/etc/modprobe.d/aliases" file but to no avail.

In the end I thought to update the firmware in my router (a linksys WRT54G version 2) and guess what?  It worked!  Version 4.21.1 is what I updated to so anyone out there with problems with this router might like to try updating.  

All the best,
Rich.

---

