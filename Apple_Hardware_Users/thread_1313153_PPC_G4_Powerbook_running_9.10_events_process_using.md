---
title: "PPC G4 Powerbook running 9.10 events process using lots of CPU"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by urschrei on 2009-11-03
I just upgraded from 9.04 to 9.10. The upgrade seemed to go smoothly, but for some reason, my fans are spinning on high constantly (even following reboot), and when I run top, I can see "events/0" constantly running at between 19.x % and about 30 %. I assume the fan situation is related to the whatever process is running, but am not sure. Is there an easy way to monitor/set fan speed from the terminal, as I am logged in remotely? Similarly, how do I determine what's causing the runaway events/0 process? I recall that there was a wireless driver issue in earlier releases, which caused events/0 to run at 100 %, but I don't think that's the problem here, since my wireless card is disabled. lshw -C network shows me:

BCM4306 802.11b/g Wireless LAN Controller
Driver=b43-pci-bridge latency=16

and that the wireless interface Wlan0 is disabled.

---

