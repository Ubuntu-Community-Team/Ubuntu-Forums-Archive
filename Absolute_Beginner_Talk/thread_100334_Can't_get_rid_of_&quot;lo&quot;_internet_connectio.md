---
title: "Can't get rid of &quot;lo&quot; internet connection"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by rasmusbp on 2005-12-07
Hi, 

I'm trying to set up my wireless network, but I'm completely unable to get rid the "lo" (local loopback) which seems to have gotten stuck in the connection window somehow. Everytime I try to enable/activate the wireless card, nothing happens. Selecting something else in "preferred device" doesn't help either.

I hope someone can help. 

Thanks.
All the best,
Rasmus

---

### Post by ChrisTheGeek on 2005-12-07
Hi Rasmas,

First of all, "lo" is essential and cannot be removed.  It doesn't represent a physical network device, but a kind of fake device that allows the computer to talk to itself.  If this sounds silly don't worry about it, just know that it needs to be there and does no harm whatsoever.

So we can help fix your problem, can you please go to a terminal window (Applications->Terminal) and type the following:

ifconfig

If you paste the output of the command here then we'll be able to see if your wireless card has been picked up or not.

Chris.

---

