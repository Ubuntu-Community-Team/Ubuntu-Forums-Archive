---
title: "laggy video and no network"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by thenoobest1 on 2005-11-19
i just installed ubuntu on my parents pavilion and it found the wireless network card (WG-311 v.2) it says its there but i cant connect to the network at all. i set up the wep tried dhcp and static ip. basically everything i can think of but still nothing. is there anything special that needs to be done before a wireless connection will work with ubuntu?

and second, the video on that pc is pretty laggy, its got an integrated video card, a 1.6 ghz processor with 256 megs of ram. and it works fine with XP, im guessing that is probably a video driver issue? if so, any suggestions?

---

### Post by Lambert on 2005-11-19
> i just installed ubuntu on my parents pavilion and it found the wireless network card (WG-311 v.2) it says its there but i cant connect to the network at all. i set up the wep tried dhcp and static ip. basically everything i can think of but still nothing. is there anything special that needs to be done before a wireless connection will work with ubuntu? 
You say it's there but is there a driver for it? Not 100% sure but this link shows a w311v2 t as not being supported.

[http://linux-wless.passys.nl/query_part.php?brandname=Netgear&zoek=brandname]("http://linux-wless.passys.nl/query_part.php?brandname=Netgear&zoek=brandname")

You can see if there is a driver for the device by typing 

sudo lshw -businfo

find the wireless device and notice the class. then

sudo lshw -C <class>

find the line for the device that starts with configuration: it will have a driver=xxxxx

If the t is not on your card and it's a pci card use lspci for info on the card.

Also if you run iwconfig does it show information such as this

ath0      IEEE 802.11g  ESSID:"xxxxx"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:1D:BC:3C
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:266966  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:2   Missed beacon:43

If not then there isn't a driver for the device that's working currently. 

This link shows ndiswrapper will work with the device.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N")

You will need your windows drivers and ndiswrapper. You can get ndiswrapper from your install cd. If you need help on installing click on lifepreserver in top panel, then 5.10 starter guide.

There are tons of posts on ndiswrapper in the forums. You can search and find how to install the drivers. Here I believe is a good link.

[http://ubuntuforums.org/showthread.php?t=81461]("http://ubuntuforums.org/showthread.php?t=81461")

---

### Post by thenoobest1 on 2005-11-20
thanks alot, im gonna give that a try in the morning.

---

### Post by thenoobest1 on 2005-11-20
ok, i did the iwconfig and all that. this is what i got:

configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s

and then

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"MSHOME"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:3A:2C:2B:26
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=39/100  Signal level=15/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

