---
title: "Installed New Hardware ~ Network Not Responding."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Toko on 2007-01-04
I recently have taken the hdd from a shuttle pc that was lacking parts, as well as the nvidia gforce 128mb graphics card, and installed it into another pc.

My previous pc was a shuttle barebone system, and the network was configured to the default ethernet port during installment of Ubuntu.

Everything was going great, xgl ran (I mainly upgraded to a different box to upgrade from XGL) but when I went to networking, no options were chosen.

So I did as many guides stated, and (I'm not sure the static ip of the dsl modem, I always used auto-config). set it to DHCP connection and enabled the device set as eth1, and then activated it, to find that there were no errors, yet no internet connection was recieved.

So after this I went into the device manager and checked the device, the network device is a wired D-Link labeled as "RTL8139 Ethernet" in the device manager.

After I figured this out I drew a blank on what to do next, I figure I'm supposed to configure the default gateway device to this device, but I'm not exactly sure how to do that, and most of the methods I've found searching for the past hour did not work (null worked).

So I've drawn a blank on how to change the gateway device to the correct d-link for it to work.

Hope someone can refer a link or help in this situation.

---

### Post by Toko on 2007-01-05
By using a module command 

modprobe via-rhine

Which activated it, but now it's going a lot slower than it should be, I'll check DNS settings.

---

