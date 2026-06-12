---
title: "wlan:ava"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-16
Hey all
I'm trying to get my wireless working on a Wanadoo Livebox
On my livebox config page it says the physical address of the USB reciever I'm using is connected
But on Xubuntu it says access point: not-associated 
when I type in ifconfig, I get two wireless devices listed, eventhough I only have one
One is wlan0 (the one I was trying to configure)
And one is called wlan0:ava
I did a google search on it but all the sites were spanish :confused:
Any ideas?

---

### Post by Sporkman on 2007-07-17
I get the same thing, but not after a reboot, only after doing

sudo ifdown wlan0

followed by:

sudo ifup wlan0

FYI I'm also running Xubuntu 7.04, with a 3com wireless card, for which I had to install the windows driver via ndiswrapper. For some reason I still can't get the thing to connect with my  router for a DHCP addr. :(

---

