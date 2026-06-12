---
title: "Help! I can't stop Wireless Autoconnect!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-14
Ok, every time i log in, i auto connect to my network...


how can i disable this?

---

### Post by DSn0wMan on 2007-07-15
In your /etc/network/interfaces file remove the line "auto <interface name>" from the interface you are connecting with.

auto eth0
iface eth0 inet dhcp

The downside to this is that you will have to bring the interface up when you want to use it.

***caution do not remove auto lo - you wont be able to do jack without a loopback

---

### Post by mikewhatever on 2007-07-15
I am sure there are better ways then removing an interface. Do you use network manager?

---

### Post by DSn0wMan on 2007-07-15
I think with network manager once you enable an interface it adds the auto line to /etc/network/interfaces so when you restart it automatically comes back up. I could be wrong, it's been a while since I used network manager.

---

### Post by ugm6hr on 2007-07-15
> **TheBlackWizard said:**
> Ok, every time i log in, i auto connect to my network...

how can i disable this?
If you are using Network Manager - try Wicd instead.  It allows you to specify whether you auto-connect to individual networks
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

