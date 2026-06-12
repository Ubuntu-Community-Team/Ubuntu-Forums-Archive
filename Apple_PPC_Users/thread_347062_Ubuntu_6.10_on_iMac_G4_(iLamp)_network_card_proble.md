---
title: "Ubuntu 6.10 on iMac G4 (iLamp) network card problem?"
date: 2007-01-26
forum: Apple PPC Users
---

### Post by robhudson on 2007-01-26
I just installed Ubuntu on an old iMac G4 700 MHz (iLamp) and everything is looking ok except for networking.  I get this in the system logs and it never acquires a network address...

eth0: switching to forced 100bt
eth0: Got link after fallback, retrying autoneg once...
eth0: Link is up at 100 Mbps, full-duplex.
eth0: Link down

Each of those messages is separated by 2 seconds, on average.

Any ideas?  Are there configuration settings to pass the network card that anyone knows of?

Thanks,
Rob

---

### Post by beanworks on 2007-02-17
Rob,

You may have already resolved this, but my first impression is, what network settings do you have on other computers? (assuming there really is a network)  Whatever is working on another computer (assigned IP or DHCP, for example) should work on Ubuntu.

If you have gnome, you can see the ethernet settings in under networking in the system menu.

Carol

---

