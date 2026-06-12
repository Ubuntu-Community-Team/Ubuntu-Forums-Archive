---
title: "[SOLVED] Basic wireless help"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-09-13
Hi guys, I've been playing with Ubuntu for a while, and just moved into an apartment with wireless. I've got to say, this seems to be one of the only things that doesn't work easily out-of-the-box.

I've read through the guides and every thread I can find, but am still confused. Are there any good links to a *very* basic set of directions on getting wifi working? Thanks.

---

### Post by Henry Rayker on 2007-09-13
This depends VERY heavily on the hardware that you have. If you have a "nice" card, it will be plug and go...some require only binary blobs, others require full drivers, and still others need ndiswrapper...

Give more information about your wireless device and I think more help can be given.

---

### Post by machavillain on 2007-09-13
Thanks for the quick reply!

Now, how do I found out what my wireless card is?

---

### Post by notwen on 2007-09-13
Copy and paste this into a terminal window and then paste back the output:
> lspci -v | grep Network
> iwconfig

---

### Post by machavillain on 2007-09-13
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by notwen on 2007-09-13
[This]("http://ubuntuforums.org/showthread.php?t=197102") seems to be exactly what you need to do.  I've heard lots of mixed reviews on Broadcom cards, but to see a HOWTO thread dedicated to this card looks promising. Best of luck to you obtaining your wireless. Nothing quite like couch surfing w/ Linux. =]

---EDIT---
60%+ have had success using the method in the link provided above. Please be sure to vote on the poll after you've finished the howto. I'll keep my fingers crossed for ya. =]

---

### Post by machavillain on 2007-09-13
I installed as directed, and now wireless doesn't even show up in Network (see screenshot). Now going to start reading through the 100-page thread to see if I can find the problem...

---

### Post by notwen on 2007-09-13
Upon searching the thread I came across 3 users who were having similar issues as you with Wireless disappearing from Network-Manager all together.  The thread author responded [here]("http://ubuntuforums.org/showpost.php?p=2015530&postcount=1012") to repeat a step.

---

### Post by machavillain on 2007-09-13
Actually just realized I don't have my Ubuntu CD with me, so I'm going to abandon this problem for today...thanks for your help, thought!

---

### Post by notwen on 2007-09-13
Np, post back if you resume this task and let us know how all turns out. Good luck. =]

---

### Post by machavillain on 2007-11-18
Solved with a clean install of Gutsy.

---

