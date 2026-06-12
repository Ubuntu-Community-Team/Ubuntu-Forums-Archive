---
title: "wifi on ubuntu"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by frreje on 2007-01-26
Hi,
I have just installed ubuntu on my pc, and I want to use internet. When I use a wire there is no problem, but I can't get my Wireless working.
Do I need to take special steps for this? Or what program do I need to install.

---

### Post by CCBalla10 on 2007-01-26
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

follow that step by step

---

### Post by OldTimeTech on 2007-01-26
my suggestion would be to use the search box above and type in wireless howto....there are many listings that come up from forum columns on the set up of wifi.

---

### Post by Threbus5 on 2007-01-26
Hmmm,
You may not need ndiswrapper, I believe that it comes pre-installed in the later Ubuntu versions.

If you are using Gnome try this:

open system configuration to networking
if the wireless card is recognized, it and your wired network card should appear. 
If the wireless card is visible in the networking configuration then you can set the Hex security code to match the one for your wireless router/access point 
If the wireless card is not visible search for howtos and additional help (sorry!)
Then enable the wireless card, give it an IP (or DNS) so that it is part of your LAN.

Remember - you can have more than one network card active at the same time..........
Try disabling the hardwire network card and Enabling the wireless card.

I found once or twice that it was necessary to enable the wireless card, then disable it, then enable it again before the machine really recognized it.

Finally, you may need to restart the machine. (May not be essential for you but I needed to do that once for both the new wireless connection and the wireless access point to fully interface.)

Take care.

---

### Post by bteck on 2007-01-27
I have similar problem accessing the Internet using my wireless network.  I installed Ubuntu 6.10 on my Acer Travelmate 6000 notebook.  Installation was smooth.  After installing, I setup wireless network using "Administration->Networking" and it seems ok.  I could connect to my router and run connection test with it.  It reported Connection between notebook and router ok, and connection to Internet also ok.  But I could not access yahoo.com or other web sites.  My firefox reported server not found all the time.  When used in WindowsXP, I have no problem.  What other settings did I miss?

---

### Post by VorDesigns on 2007-01-28
Search DWL-G650 and look for my posts on manually associating the card.  I may help.
The directions assume that the card is recognized by the OS and they are derived from two weeks of trying.

---

