---
title: "WIFI does not work after upgrade"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by bramberg on 2007-06-01
I have been running Ubuntu 2.6.17-10 on a SONY Vaio laptop and hve now upgraded to 2.6.20-16. The problem is that after upgrade Ubuntu does not recognize my WIFI interface. I get this message when I try to configure the interface: SIOCGIFFLAGS error: No such device. The inteface used to be listed as eth1 wireless, after the upgrade there are two interfaceses wlan0 and eth0 bothe indicated as wired connection. Any ide how to get my wireless card to work?

---

### Post by mlentink on 2007-06-01
You might want to try to update your linux-restricted-modules to 2.6.20-16 as well, as they don't get updated automatically. Search Synaptic for them.
That worked for me.

---

