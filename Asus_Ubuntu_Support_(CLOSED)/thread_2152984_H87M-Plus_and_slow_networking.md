---
title: "H87M-Plus and slow networking"
date: 2013-06-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mbott on 2013-06-09
I just updated my desktop with the new H87M-Plus motherboard and I'm now experiencing slow/inconsistant networking under 12.04 LTS.  Originally I was using a Belkin F5D7000 which is the Broadcom BCM4306 chip.  This worked with my previous motherboard and delivered up to 615 Kbps throughput as reported by Ubuntu.  Connection Manager listed the speed as 54 Mb/s with this card.  When installed in the H87M, Connection Manager would report the same spped, but throughput would be anywhere from 50 Kbps to 550 Kbps...when it worked at all which was 50% of the time.  

Adding a cable to the router to get a 100 Mb/s link showed little improvement in throughput.

Today, just for grins, I replaced the Belkin PCI wireless network card with a Netis WF-2113 PCI-E adapter.  Connection manager now reports a 144 Mb/s link, but with no increase in throughput.

Any suggestions on my next step to try and resolve this?

TIA!

-- 
Mike

---

### Post by mbott on 2013-06-13
In case anyone is interested, some stability has been restored to this system by removing Network Manager and replacing with Wicd.  Now I'll work on getting -n speeds

-- 
Mike

---

