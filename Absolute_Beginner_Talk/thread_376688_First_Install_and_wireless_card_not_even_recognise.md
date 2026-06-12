---
title: "First Install and wireless card not even recognised"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by simonfoley on 2007-03-05
I am a first time installer of Ubuntu and I am having a real uphill struggle with my wireless card.  My laptop has the following Wireless Lan Card 

NetVision IEEE 802.11b
Wireless LAN CardBus Card

I have looked everywhere for whether this device is supported but it seems that this quite a rare card and therefore it is hard to find information.  

I can not even get Ubuntu to recognise that I have the card plugged in.

I have done a search at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)
and it is not recognised at all.  I also followed the guide and had a go at each of the stages.

I tried google and got nothing of help.  I have Ubuntu 6.10 installed and everything else seems to be working fine. 

Any ideas of the stages I should go through?  As maybe is a BUS problem.

I tried to run *lspci -v | grep subordinate*

and got the information that I should maybe add 

*pci=assign-busses*

to my kernel boot line?

I am not so linux minded and do not know how to do this or even if I am heading in the correct direction.

However, I am not even convinced that this could be problem.  Any ideas of this card?

Simon

---

### Post by george29 on 2007-03-05
you might try posting this request in the ubuntu/networking forum... might be seen by more people who can help you.

---

### Post by PartisanEntity on 2007-03-05
Perhaps it is better to ask the mods to move the thread for you though instead of posting it again a 2nd time :)

In my experience getting wifi to work was the hardest part for me in the beginning, but not because it is so difficult, but because as a newbie I didn't anything about Linux at all. Nowadays it takes about 3-4 mins to get wifi working after a fresh install.

I am not familiar with your wifi card but be prepared to try out quite a few methods and perhaps you might need to reinstall a ubuntu once or twice until you get the hang of it and until you find a method that works for you, that's how it was for me.

Good luck.

---

