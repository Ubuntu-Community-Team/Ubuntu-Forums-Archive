---
title: "usb wifi adapter that works on ppc?"
date: 2005-04-03
forum: Apple PPC Users
---

### Post by luna6 on 2005-04-03
If anybody has had a positive experience with a particular brand of a usb wifi adapater for ppc, or knows what works on the ubunto hoary for ppc, please let me know. I love linux on my powerbook, but feel frustrated I cannot use it on wireless networks. I am willing to purchase a usb wifi adapter, if there is a particular brand that installs and works reliably...thanks

---

### Post by nyqo on 2005-04-03
I have had very good success with my DWL-122. Setup instructions are also posted in this forum, check for my previous posts.

---

### Post by luna6 on 2005-04-03
thanks man, reading now.....

---

### Post by prio on 2005-04-04
DWL-122 setup was very easy under warty, plugged it in and ran 
dhclient wlan0
On hoary though I have to run the following script

-- Cut here --
#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=opensystem
sudo dhclient wlan0
-- Cut here --

I found this script on these forums so shout out to the guy that wrote it. (reposted it as it took me a while to find it). The DWL-122 does work nicely though.

---

### Post by Elsifer on 2005-04-08
[QUOTE=luna6]I love linux on my powerbook, but feel frustrated I cannot use it on wireless networks. I am willing to purchase a usb wifi adapter[/QUOTE]

Why not just get a pcmcia adaptor? I'm willing to be that the setup would be a lot easier than a usb adaptor. And nearly 85% of the cards out there are supported.

Cheers
Chris

---

### Post by luna6 on 2005-04-08
would be nice but my powerbook G4 12" with 1.33 ghtz processor doesnt seem to have pcmcia card slot.

---

