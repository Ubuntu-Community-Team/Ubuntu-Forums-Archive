---
title: "Buffalo WLI-CB-G54A on Kubuntu 6.10"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by leamphil on 2007-04-01
First install of Kubuntu on IBM TP 600x yesterday and coming to grips with WLAN.  Been reading the hits on Google and I (think I) have managed to:

1) blacklist BCM43xx
2) Use ndiswrapper on the driver for my card off the Buffalo site (ndiswrapper -l shows it installed and hardware present)
3) Get the lights flashing on the card :) 
4) Get the correct ESSID, frequency, access point mac address showing on iwconfig
5) Check that I've set the right WEP key by doing sudo iwlist wlan0 enc (and I sure it is the right one as I've recently been configuring some windoze clients)
5) Set what looks like the right static ip address set
6) See my AP on iwlist wlan0 scan

But :(  I cannot ping my home network.

Suggestions please

---

### Post by leamphil on 2007-04-03
:)  .. got connected by:

1) Took all the network definitions out of /etc/network/interfaces
2) Tried with a test access point without WEP enabled - connected fine using KNetworkManager
3) Put simple WEP key on Access point & it failed to connect
4) Entered "sudo iwlist wlan0 enc" whilst this connection was failing & spotted a very strange key set
5) Retried with KNetworkManager, using sudo iwconfig wlan0 key s=<correct key> whilst it was trying to connect - and it worked !
6) Did the above to my production access point and connected successfully

---

