---
title: "ktorrent firewalled"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by sundar261 on 2007-12-22
Hi,

There are no incomming connections to ktorrent.  I see a message that I would have been firewalled.    I tried loading the UPnP plugin but when I open the plugin there are no port forwarding.  Rescan also does not help

Any help in resolving this issue would be helpful.  Torrent downloads are crawling :(

Regards,
Sundar

---

### Post by bone2006 on 2007-12-24
get firestarter "sudo apt-get install firestarter" should do it.   This is a gui for the firewall.
You need to allow the ports to come in 6881 through 6889.  Do port forwarding on your router as well instead of using UPnP

---

### Post by sundar261 on 2007-12-26
> **bone2006 said:**
> get firestarter "sudo apt-get install firestarter" should do it.   This is a gui for the firewall.
You need to allow the ports to come in 6881 through 6889.  Do port forwarding on your router as well instead of using UPnP

Thanks!! I had to use encryption as there blocking done for the seeding (ISP??)

---

### Post by bone2006 on 2007-12-27
I have encryption turned on as well, which I believe comcast was doing things to slow down the traffic

---

### Post by bodhi.zazen on 2007-12-27
If you are running KDE, you may want to use guarddog over firestarter.

Both are fine gui tools to configure your firewall.

---

