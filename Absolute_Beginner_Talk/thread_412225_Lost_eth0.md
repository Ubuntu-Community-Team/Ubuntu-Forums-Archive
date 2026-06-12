---
title: "Lost eth0"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-04-17
Suddenly eth0 has disappeared. I have a Lenovo N100 with a Broadcom 4311 card. After many attempts, I finally got it working in Edgy with ndiswrapper (thanks to this forum). It's worked fine for months, but suddenly I've lost my wireless. There is no Wireless Connection in Network Manager, if I enter commands such as 
 
sudo ifdown eth0 && sudo ifup eth0
I get 
ifdown: interface eth0 not configured

When I type lspci the Broadcom card is still recognized (and the driver is still listed).

Eth0 isn't listed when I try to use Nettools.

How do I restore eth0 and my wireless capability? 

Thanks.

---

### Post by Seisen on 2007-04-17
If its a wireless card it should come up as ath0 or wlan not eth0.

---

### Post by drs305 on 2007-04-17
Well, it's an internal card. In any case, I have lost the automatic logging (or manual for that matter) on to wireless and no Wireless Connection in Network Manager. I used to run commands with eth0 without getting error messages, now I can't. But I don't use the terminal often except for installing things. I'm pretty ignorant about what things in linux are called.

---

### Post by N Clement on 2007-04-17
Does iwconfig tell you anything interesting?

---

### Post by drs305 on 2007-04-17
> **N Clement said:**
> Does iwconfig tell you anything interesting?

lo        no wireless extensions.
eth1      no wireless extensions.
sit0      no wireless extensions.

By the way, how do you put terminal commands/results inside boxes. I thought it had something to do with the # symbol ...

Thanks.

---

### Post by Seisen on 2007-04-17
Just click on the # sign and put what you want between the "CODE" in brackets.

---

### Post by N Clement on 2007-04-17
I'm not very familiar with ndiswrapper anymore, since I was fortunate enough have a card that Ubuntu recognized right away, but I would use ndiswrapper commands to try to get some feed back that way.  Maybe try man ndiswrapper?

---

### Post by Austin_KW on 2007-04-17
is there a hardware enable switch? sometimes these get knocked/bumped to the off position

---

### Post by drs305 on 2007-04-18
> **Austin_KW said:**
> is there a hardware enable switch? sometimes these get knocked/bumped to the off position

There is a switch, but it is on and the wifi works fine on XP. 

I think the lack of solutions is probably because of the way I titled it. I should simply have said "I've lost my wireless" since I don't have the wireless connection in Network Manager that I had when it worked. I REALLY don't want to go through the entire ndiswrapper solution again and had hoped that there would be a simple solution to restoring the wireless connection in NM.

Thanks for the suggestion anyway.

---

