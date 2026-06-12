---
title: "Wake-On-Lan with MacMini"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by wojtekz on 2007-04-22
Hi,

I have a PPC-based Mac Mini and tried to enable wake-on-lan without any success yet. I did the following:

ethtool -s ethX wol g
/etc/init.d/networking restart
/sbin/halt -hdp

When sending the magic packet from another machine nothing happens. Does anyone know how to enable wake-on-lan with PPC and Ubuntu?

Thanks in advance,
Wojtek

---

