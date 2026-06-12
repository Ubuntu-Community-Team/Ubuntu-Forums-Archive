---
title: "default gateway"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Riffer on 2008-01-20
[SIZE="2"]I'm trying to set up a couple of older machines using Ubuntu in my classroom.  I was hoping to try out Xbuntu as it has less system requirements and would hopefully make these older machines perform well.

The schools network is DHCP but to use the web or to outside of the LAN   it uses a default gateway, that has a static IP and port number.  I can set that quite easily in Ubuntu using the tool  "Network Proxy " found under --System--Preferences.  In Xbuntu I can't find a similar tool.  

So my question(s), is there a similar tool in Xbuntu that I can set the default gateway?  Or if not how can I set this gateway?                                [/SIZE]

---

### Post by bwhite82 on 2008-01-20
> sudo ip route add default via 192.x.x.x

-Cheers

---

### Post by Riffer on 2008-01-20
Thanks :).  Will that command set the gateway permently?  Or will it have to used every time you boot up?

---

### Post by bwhite82 on 2008-01-20
It should do it permanently, however, if not, you can also edit the /etc/network/interfaces file.
After open (use nano or your preferred editor), find the desired interface (eth0, eth1?), and then add the following option:

> gateway 192.x.x.x

---

### Post by Riffer on 2008-01-20
Ok thanks.  I'll give that a try :)

---

