---
title: "Wireless card on laptop"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by JMV290 on 2007-03-26
>  Network Card  
Model: Broadcom 54g MaxPerformance 802.11g - Packet Scheduler Miniport 
Driver: bcmwl5.sys
Wednesday, October 20, 2004
Supported 
 


That's what HP Help and support center says about my wireless card.


Will the wireless card work on Ubuntu?  Where can I get ubuntu drivers if they aren't installed.


I'm going to install Ubuntu once I get a larger harddrive.

---

### Post by Sandlst on 2007-03-26
It sounds like you have the same card I do.  Broadcom cards can be annoying to set up, but it is easily doable.  I would try a live cd first, after you boot it up, opening a terminal (Applications/Accessories/Terminal) and typing ```
dmesg
```You should see some entry for your wireless card, Broadcom, followed by a number like 4318 (in my case)  If you dont see it, try ejecting the card, plugging it back in, then run the command again, it should pop right up.  After you find that, do a forum search on the specific model # you now know, and the results should hopefully help you out.  Good luck, post back if you have any problems!

---

