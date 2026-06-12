---
title: "Unable to get wireless working!"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by boixter on 2008-01-26
Hello im new here!
I can't seem to get the wireless to work! ):

When i enable roaming on network manager, it manages to detect my wireless router, but i cannot connect to it. Rather, when i connect to it, it asks me for passphrase, and i typed in a 10-digit encryption key which i am very sure is correct because i can connect using this WEP key on my windows laptop. However, after a while the message just pops back up.

If i connect through 'connect to other wireless network' on the drop down menu of the network manager, i get a connection but the strength of the connection is shown to be 0% and there seems to be an invalid IP address like 0.0.0.0 

If i do a 'manual configuration', and disable roaming mode, inputting my ESSID, my network password as WEP (hex), and using DHCP and save, then ticking the wireless connection, then later nothing happens. 

I've tried using wifi-radar but somehow it only shows all the 802.11b networks in my vicinity and not the 802.11g networks (which my wireless network is one of). I've tried manually adding my network in but it showed that it was unable to acquire an IP address.

I'm using Linksys Wireless USB Adaptor WUSB54G (version 4) and i assume that the driver is working correctly because it is able to detect the other networks. But I've tried connecting to the other unsecured networks and it doesnt seem to work ask well. 

This has been such a headache and im getting frustrated coz i wiped out my windows on it and am enjoying the ubuntu OS but if i cant get on the net, im going to have to uninstall it!

Please help
and Thanks much!

btw im using ubuntu 7.10 on an AMD athlon 1800+ with more than 512mb ram (i forgot exactly how much haha)

---

### Post by Tekno_Cowboy on 2008-01-27
just because it's showing networks, it doesn't matter that the driver is working properly. Try searching the forums for your network adapter.

---

### Post by ugm6hr on 2008-01-27
Confirm some info might help:

```
lshw -C network
lsusb -v
ifconfig
iwconfig
iwlist scan
```

However, I gather your device is a Ralink RT2500USB chipset.  So the driver (in Gutsy) is the problem.

Potential solutions:
1. latest rt2570 driver:
[http://ohioloco.ubuntuforums.org/showthread.php?t=588045](http://ohioloco.ubuntuforums.org/showthread.php?t=588045)
2. ndiswrapper: 
[http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/](http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/)

Hope one of those gets you going.

---

