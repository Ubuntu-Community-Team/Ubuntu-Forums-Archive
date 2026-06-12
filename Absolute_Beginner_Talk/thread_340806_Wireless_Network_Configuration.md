---
title: "Wireless Network Configuration"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by tmptplayer on 2007-01-17
I am trying to connect to a wireless network in my house that was set up using a linksys wireless G router with WPA2 encoding.  The ESSID is two words with a space in the middle similar to "Larry Wireless".  I can other wireless networks through systems->network, but I am unable to connect to my network.  On a side note- when I do ```
iwlist scan
``` I can see my wireless network listed, but even when I try to modify the network interfaces file manually I can't get it work.  I think it is because the space- assuming I can't change the name of the network, are there any fixes?  Thanks

-BS

---

### Post by Zaffe on 2007-01-17
Could be the encryption WPA2, do you have wpasupplicant?

here is a tutorial: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by tmptplayer on 2007-01-17
> **Zaffe said:**
> Could be the encryption WPA2, do you have wpasupplicant?

here is a tutorial: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Thanks- I'll give it a shot.

---

