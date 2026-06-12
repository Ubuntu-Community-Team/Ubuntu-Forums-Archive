---
title: "Network Manager"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Soarhead on 2007-05-08
I have a problem with wireless connection which I suspect is down to Network Manager. I have this applet running and with a normal mouse click I get Wired Network and Manual Configuration as the only two options. (I say normal click since I'm left handed). Left click (for me, Right click for normal people) gives Enable Networking, Connection Information and About  - selecting this tells me that the version is 0.6.4. 

When  I had a wireless card installed it would be seen using System|Administration|Network - but Network Manager would only show this limited set of information, unlike what I see in the general Ubuntu documentation for 7.04. If I disconnected the ethernet connection I would lose all network connectivity no matter what I did. I used to have Wireless Assistant installed, but uninstalled it some time ago to see if it made a difference - it didn't. 

Anyone got any ideas?

---

### Post by MrPyro321 on 2007-05-09
Your post was a tad bit confusing but I assume that your wireless card is installed?
If so and your not seeing it when you left click (right for you) on the network manager in the system tray then:

Make sure that roaming is enabled for your wireless card.
System|Administration|Network > then click on the properties for your card. And click "Enable Roaming Mode"

---

### Post by Soarhead on 2007-05-09
Hi 

Sorry if  I confused - I tried not too! 

I installed 7.04 when the update became available, at that point I had 

Wireless Monitor 

A Belkin wireless card with RAlink chipset

An ethernet connection to the router.

At this point I could see both connections in System|Administration|Networks

However, I could not see any change in Network Manager. I then uninstalled Wireless Monitor to see if there were any conflicts. This made no difference. I then unplugged the ethernet - now I lost all connection to the network but System|Administration|Networks could see the card. 

More out of orderliness than anything else I then removed the card from the PC. At no time did I see any change in Network Manager.

---

