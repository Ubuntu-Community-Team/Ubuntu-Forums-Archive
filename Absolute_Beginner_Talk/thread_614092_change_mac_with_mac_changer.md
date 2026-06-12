---
title: "change mac with mac changer"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by powerfulx100 on 2007-11-15
Current MAC: 00:01:3e:14:cb:b1 (Pc Partner Ltd.)
ERROR: Can't change MAC: interface up or not permission: Device or resource busy

---

### Post by ray bot on 2007-11-15
You can't change your mac address while the network interface is connected, and you need root priveleges to do it.  Disconnect the network, run sudo macchanger ethx (replace x with the correct number, e.g. eth0 or eth1), and reconnect the network.
There's also a graphical frontend for macchanger that you might want to check out.  It's called macchanger-gtk.

---

### Post by powerfulx100 on 2007-11-15
i tried disconnecting(unplugging cable) it doesn't work. how do i disable device please? thank you

---

