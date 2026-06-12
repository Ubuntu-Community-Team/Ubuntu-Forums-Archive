---
title: "IBM 390X Network Detection"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by jatnic on 2006-09-14
I am a beginner with Linux and Ubuntu. I have installed 6.06 desktop version on an old IBM 390X Thinkpad. It seems to install well, but it is not loading the driver for the network cards that I have installed. I have a 3Com Megahertz 10/100 LAN PC Card with XJACK Connector model 3CSFE574BT and I have also tried a Linksys Wireless-G 2.4 GHz, 802.11g Card.
In both cases the Network tool indicates that it sees the piece of hardward but I can't get an IP address. I had a fried look at it, but in the log it indicated that it fail to load the selecter driver.
Any suggestions?

---

### Post by benfindlay on 2006-09-14
I'd recommend using Synaptic Package Manager to install ndiswrapper and networkmanager.

Ndiswrapper allows your pc to use windows drivers with wifi cards, and networkmanager gives you much more detailed information about your network devices than the normal networking options

Hope this helps

---

