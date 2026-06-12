---
title: "Wireless Disaster (Netgear WG111V2)"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by hrkac on 2006-08-30
Okay, I'm close to giving up totally. This is my first shot at Linux and I can't get my wireless USB adapter (Netgear WG111V2) to work under Ubuntu. I've tried installing the drivers through ndiswrapper, and they show up like they've been installed, but when I try to set up the network under Network Config it hangs and won't connect. The device itself will blink once then nothing. I've tried about everything I've found on these forums and elsewhere but no luck, but hopefully this time it will work. Any information you think would help please ask and I'll post it as soon as I can.

iwconfig results:
lo       no wireless extensions.
eth0     no wireless extensions.
wlan0    802.11b/g ESSID:"xxxx" Mode: Managed Channel=13
         Access Point: Not-Associated Bit Rate=11 Mb/s                  Sensitivity=4/6 Retry:on   Fragment thr:off
         Link Quality:0 Signal level: 0 Noise level: 0
         Rx invalid nwid: 0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ndiswrapper -l results:
net111v2
driver present, hardware present

---

