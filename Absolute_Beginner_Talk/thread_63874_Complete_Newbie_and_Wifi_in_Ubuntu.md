---
title: "Complete Newbie and Wifi in Ubuntu"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by Connor2003 on 2005-09-09
Hi All,

well yet another Windows crossover! I have just downloaded the Live CD Version of Ubuntu. I also have the hard drive version waiting in the wings but I thought I would see how the live version goes. From what I can see I have a lot to learn especially having read through these forums.
Anyway onto my problem. I have read endless topics on configuring Ubuntu for a wireless network but they all seem to require a little knowledge of Linux and I have none. From what I can see Ubuntu can see my wireless card as it lists it in the Device Manager as a Texas Instruments wireless card. I then go to the Network configuration tab and insert all the details for my WLAN including the ESSID and the WEP Key and then activate the network. Thats about all I know how to do. As you have guessed it doesnt work. I have read topics on a program that can utilise Windows drivers but I dont know how to pull that off this live cd.
Basically is their anybody willing to talk a Newbie through the whole steps and explain to me in a way that I might be used to. I can Copy and Paste all day!  :grin: 
Once I am on the internet with Ubuntu I can then read threads galore and try and figure Linux out from the bottom.

Thanks for any help.

Chris.

---

### Post by Steve1961 on 2005-09-09
First of all, welcome.

Second, there's a few things you need to do when configuring wireless cards in Ubuntu.  The first is identifying your chipset and version rather than the make of the card.  You should be able to find this out by typing lspci -v into the terminal and finding the appropriate entry.  You can also try looking it up at the sourceforge ndiswrapper website [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Once you know the chipset the next stage is finding out if there's a linux driver available.  If not, then you'll need to use ndiswrapper.  Basically this allows you to use the windows drivers for your card in Ubuntu, but as you sometimes need to experiment with different versions of drivers and ndiswrapper a linux driver is always preferable if one exists.

There's lots of information on this forum for setting up ndiswrapper and you should start by reading this [https://wiki.ubuntu.com/WiFiHardware](https://wiki.ubuntu.com/WiFiHardware)  What you need to do then will depend on the make of your chipset, but one step at a time. if you get stuck just ask for help here.

---

### Post by Connor2003 on 2005-09-09
Hi Steve,

thanks for the quick reply. I'll give what you said a whirl later on and let you know. Off topic a little would you say I have made the right choice to use this Distro of Linux. My main reasons for choosing this Distro was the large amount of support that seems to follow it plus just looking at the live cd it seems that the package is very well put together.
Ok cheers for now.

---

### Post by Steve1961 on 2005-09-09
I can only go off my own experience, which to be honest is only about 3 months worth.  But I started off looking at Xandros, Fedora and Ubuntu and I found Ubuntu to be the most straightforward.  It also has some of the best documentation available and the community support is second to none.

---

