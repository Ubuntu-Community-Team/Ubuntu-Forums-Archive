---
title: "Beginner having problems with intel(R)PRO 2200 BG"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Linda on 2007-07-06
I'm a beginner with Linux.  My son is a developer, but lives in TX and I'm in FL.  I'm having problems setting up my wireless.  My Toshiba laptop has Intel(R)PRO 2200 BG for the wireless.   I'm also having problems with ICQ.  I have an ICQ account, but when I try and set it up through Gaim, it says my password is incorrect, but I know it's right.
I would greatly appreciate any help.

Linda

---

### Post by swisscow on 2007-07-06
Which version of Ubuntu are you using?

The reason I ask is that I am using Feisty and I have this exact wireless card in my laptop and it works straight out of the box. Come to think of it, it did with Dapper as well. You could check the output of ```
lspci
``` in a terminal to confirm your wireless card model and then move forward from there.

Also you could check if network-manager is running (or knetworkmanager in kubuntu). Have a look for an icon on the toolbar (in Kubuntu looks like a bar graph). If you can't find it have a look in Synaptic to see if they are installed and if they(it) is then have a look in the menus and click on it to make sure it starts

Sorry this isn't much help, but as I have never had to do anything with wireless I don't really know much about it.

---

### Post by fazavon on 2007-07-06
My old notebook had an Intel 2200 bg and I never had an issue, but he is right check your network manager, then the... i believe ipw2200 is the name of the packet in synaptic.

If both of those are on and or installed it could be that your card is on its way or is already dead.

//j

---

