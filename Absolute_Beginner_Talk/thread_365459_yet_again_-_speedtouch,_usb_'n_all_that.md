---
title: "yet again - speedtouch, usb 'n all that"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by grhughes on 2007-02-19
I need a little help getting connected thru my speedtouch 330. This is a usb adsl modem. I've followed the HowTo on this site, but it doesn't work on this fresh install of 6.10.
1. Firmware does not load
2. There is already a kernel-mode driver loaded on start-up, along with the 'usbatm' module
3. I can't find a device node for the modem. The ppp 'provider' file seems to need one.

I've done a fair amount of browsing and I'm now frustrated. There are lots of speedtouch how-tos out there, unfortunately there are no why-tos. If anyone can help with this in a specific way I would be very grateful.

---

### Post by teaker1s on 2007-02-20
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

---

### Post by grhughes on 2007-02-21
Thank you teaker1s!.
The problem was simply that the firmware was in /usr/lib/hotplug/firmware, where dpkg installed it. Now it is in /lib/firmware, and all is well. Pity I ordered a router from amazon but at least it will get the kids off my back/PC. The most frustrating thing about it was not knowing how pppoatm connects without any device node, just using VCI/VPN numbers. Still don't know :) 
Thanks again

---

