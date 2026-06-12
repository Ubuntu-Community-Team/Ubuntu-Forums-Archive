---
title: "D-LINK DWL-122 rev b"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by oscarwilde on 2007-04-25
Hello. I have a D-Link DWL-G122 rev b1  Wireless usb adapter that runs under Ubuntu Edgy just fine but may not run under Ubuntu Feisty has anyone got any ideas how to get it up and running under Ubuntu Feisty before I take the plunge and upgrade.

Thanks very much for any help or advice.

---

### Post by udayan18 on 2007-04-25
evn my DLINK GLB-502T isnt working...ne help wud b much appreciated

---

### Post by syphron12 on 2007-05-20
DWL-G122 Rev.A2 not working under Ubuntu Feisty Fawn 7.04. Any help would be appreciated.

---

### Post by Kobalt on 2007-05-21
Aren't these cards based on the [RT73]("http://ubuntuforums.org/showthread.php?t=400236&highlight=dwl-g122") chipset ? (check with *lspci* maybe)

---

### Post by rvergara on 2007-07-08
I am using the dwl-122 without major problems under 7.04.

I plugged it in and saw that wlan0 was displayed when ifconfig was run, however I saw that my dhcp server did not assign an ip to my ubuntu box, so I just cycle down and up wlan0 (ifdown wlan0; ifup wlan0) and voila... I had the dwl-122 working perfectly.

I always have to cycle wlan0 when I boot the computer but it is a very small hitch.

Hope this helps

Ramiro

---

### Post by apenalo on 2007-08-13
Ramiro, are you sure it works for you??

I tried it in v7.04 and when I do that you did, Ubuntu tries to connect, and even asks me the WEP key, but then it just gives up and doesn't connect!

Did you do anything else (like installing a patch)??

---

