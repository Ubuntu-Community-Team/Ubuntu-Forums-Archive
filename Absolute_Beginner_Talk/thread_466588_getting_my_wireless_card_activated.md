---
title: "getting my wireless card activated"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Neezer on 2007-06-06
I have a trendnet 802.11b PCI wireless card. I want to connect to a network that has wpa encryption on it. I have never had this problem before cause I was conected directly to the router. now, I have moved into a house for the summer, and my computer is not near the router. I am running 7.04. Some straight forward help would be much appreciated I am not that good at command line stuff, so if someone would be willing to walk me through the process, that would be just awesome!.

Thanks
Neezer

---

### Post by esavato on 2007-06-06
If your card is B only, it is unlikely to support WPA encryption.

---

### Post by Neezer on 2007-06-07
I kind of figured that I would need to get a new card. Do any of you have any suggestions as to which card I should get? I will probably go with a G card, but I would like to know some quality cards that don't have compatibility issues with Ubuntu.

---

### Post by mlentink on 2007-06-07
Generally cards based on the Atheros and Ralink chipsets should work out of the box. So do the Intel 3945ABG and most Broadcom cards and cards with a different brand but based on the same chipset. There&#347; a list somewhere on the net, but I forgot where.

---

### Post by esavato on 2007-06-07
I found the following post...
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Which points to a few places that list compatible cards...

This page lists many manufacturers and states if they work "out of the box" or not
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Another helpful page.
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

Hope this helps!!

---

### Post by muguwmp67 on 2007-06-07
I'm using a Trendnet TEW-501PC with a/g and it works beautifully.  I didn't expect WPA to work without a great deal of configuration, but with feisty's WLAN browser it was a piece of cake.  I did have to enable restricted drivers, but otherwise no problems.  The card cost me about $20.

---

### Post by Neezer on 2007-06-08
ok. I got a new card. a linksys wireless G card. I got my machine to recognize the card, but now I get no signal from the router. i know for a fact that the router is good because i am in the same room as it is, and i have a laptop hooked up to the network wirelessly.any suggestions on how to get signal from the router?

---

### Post by Neezer on 2007-06-09
I got my wireless card activated, but I am having problems with the oruter. it is a Siemens speedstream 6250. I am not reading any signal from the router, and then i tried restarting the router, and that didnt work either. do I need to get a new router? also, this is a DSL router, so will a linksys router work?

---

### Post by ugm6hr on 2007-06-09
If the router works with a laptop, there shouldn't be an issue.  Try telling us exactly how far you have gotten with connecting - there will almost certainly be a solution.

Things to include:
*lspci* (will list the wireless chipset as Network Controller)
*ifconfig* (will list all network connectors)
*iwconfig* (will list wireless connections)

How are you trying to connect to the wireless network?  Using Network Manager, or some other way? Which version of Ubuntu are you using?

---

