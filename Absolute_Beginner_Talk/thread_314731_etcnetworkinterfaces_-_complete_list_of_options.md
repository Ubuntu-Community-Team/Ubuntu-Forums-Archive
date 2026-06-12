---
title: "/etc/network/interfaces - complete list of options?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-08
Hi, quick question - does anyone know where I could find (or have a  link to) a complete list of options (wireless-essid, wireless-key, etc)? I tried man network but it doesn't have anything about wireless interfaces.

---

### Post by devnulljp on 2006-12-08
The bits you need are 
wireless-essid <your ESSID goes here>
wireless-key <your wep key goes here>

So, a final interfaces file would look like:

auto eth1
iface eth1 inet dhcp <or static>
network ip.address.goes.here
dns-nameservers ip.address.goes.here
wireless-essid ESSID
default-gateway ip.address.goes.here
wireless-key wep key goes here

here's some helpful info [http://llaic3.u-clermont1.fr/~mr/linux/configreseau_en.shtml](http://llaic3.u-clermont1.fr/~mr/linux/configreseau_en.shtml)

---

