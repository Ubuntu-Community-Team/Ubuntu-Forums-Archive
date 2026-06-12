---
title: "Help with Netgear WPNT511 Wireless Card"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by wesb on 2007-10-15
I have a problem. 
I used Danni's guide originally for the WPNT511 or similar cards for that chipset.
I installed ndiswrapper from the synaptic manager and managed to get the driver isntalled.
> 
:~$ sudo ndiswrapper -l
netani : driver installed

Also the dmesg command shows this:
> [  860.920000] pccard: CardBus card inserted into slot 1

Both lights are on solid on the WPNT511 and I am lost at this point. What do I need to do point the driver at the network card? Sorry for all the questions I am a ubuntu n00b trying to get away from Windows. :)
Thanks in advance.
-WesB

---

### Post by mikeyphi on 2007-10-16
Does the wireless card now appear under System/Administration/Network?
If so enter appropriate settings
If not - you need more help than I can offer!

---

### Post by wesb on 2007-10-18
No it doesnt. How do I tell Ubuntu the cardbus is a network card?

---

### Post by wesb on 2007-10-18
In the device manager I see 
AGN300 802.11 a/b/g True MIMO Wireless Card
Airgo Networks

Does this mean the driver is installed or is the machine finding the card?

---

### Post by Skigi on 2007-10-24
I think it's just knowing that it's there. I've been having the same problems, following this tutorial:

[http://ubuntuforums.org/showthread.php?t=262465](http://ubuntuforums.org/showthread.php?t=262465)

And so far no luck.

---

