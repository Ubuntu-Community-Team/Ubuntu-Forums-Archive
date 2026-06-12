---
title: "wireless deterioration"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by dsbw on 2007-09-11
OK, seriously, what is going on?

I've got this situation that wherever I move my router to, my wireless card picks up a signal for a few days, then deteriorates until it finally won't connect anymore. So I keep moving the router closer and closer to the Ubuntu desktop, but the cycle keeps repeating. I've done this three times, each time moving the router closer and closer.

Eventually, I know I'm going to end up with the router on top of the computer and being unable to connect. At one point, the router in the current position had a 100% signal (you can read about that in my smash hit thread "Wireless Tango Foxtrot"). Now it's 26%, but only after I sacrificed a chicken.

I don't even get how this is possible. The signal from the router (Belkin N1) isn't changing as far as any of the other (non-Ubuntu) wireless stations are concerned. What is it about the Ubuntu wireless driver (Atheros chip on the wireless card) that causes it to constantly re-evaluate the signal with increasing bitterness?

---

### Post by KCPokes on 2007-09-11
I feel your pain.  My wireless has been the one sore spot on my Ubuntu laptop.  Sitting in the same general vicinity I have roughly 40% signal strength, whereas I can be two floors away with Windows and the signal is "excellent".  I've also found that transferring large files causes the connection to just drop with the only means of resolution being a reboot.  Changing from Network Manager to Wicd seemed to improve that a bit but it still happens.  From reading and performing my own tests with different hardware, it does seem to be related to specific chipsets rather then ubuntu in general (I have an old Linksys draft-g card that will not drop the connection for anything).  In general it seems to be related to Broadcom chipsets, or in my case Realtek cards.  

How happy I'd be if there was an easy solution.

---

### Post by dsbw on 2007-09-12
> **KCPokes said:**
> From reading and performing my own tests with different hardware, it does seem to be related to specific chipsets rather then ubuntu in general (I have an old Linksys draft-g card that will not drop the connection for anything).  In general it seems to be related to Broadcom chipsets, or in my case Realtek cards.

The card? Oh, man, that sucks. I bought this card specifically because it was said to work perfectly in Ubuntu.](*,)

---

