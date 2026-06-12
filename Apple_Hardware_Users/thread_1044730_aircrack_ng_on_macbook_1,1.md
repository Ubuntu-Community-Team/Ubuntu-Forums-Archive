---
title: "aircrack ng on macbook 1,1"
date: 2009-01-19
forum: Apple Hardware Users
---

### Post by andrewbossie on 2009-01-19
can i ue aircrack-ng on my 1st gen macbook? and if, so can someone tell me where i can find how to set it up?

---

### Post by ssorc on 2009-01-20
The Airport Express card in the Macbook is not compatible with aircrack-ng. 

Your best bet would be to consider using one of the compatible adapters in the list of compatible hardware (eg. a USB wifi adapter) on the aircrack wiki.

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

---

### Post by snowy16 on 2009-02-24
I was able to get it working on my Macbook 1,1.  Install madwifi-tools and aircrack-ng.

sudo apt-get install madwifi-tools aircrack-ng

Execute the following command which will create ath1 in monitor mode.

sudo airmon-ng start wifi0

Then you can start sniffing with airodump.

sudo airodump-ng ath1

---

### Post by ChibiLink16 on 2009-02-24
well i read somewhere that the airport extreme cards in the new intel macs have a different chipset than the original power books so monitor mode isn't supported. dont know about older models

---

