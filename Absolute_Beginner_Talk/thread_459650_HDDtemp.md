---
title: "HDDtemp"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-05-30
Ok...so I installed hddtemp in order to monitor my temps via sensors-applet...but why does it need an IP address and port # in order to run it daemon? Is this a security risk?:confused:

---

### Post by araz on 2007-05-30
Hello,

> (...)but why does it need an IP address and port(...)
Because ehernet is a way of sending info between processes and computers (in same network). I guess they use this way to allow users to monitor several temps of other computer in the network (its a more versatile way of transmit this kind of info).

> (...)Is this a security risk?(...)
Personally I don't see it has a risk but if you want to reduce the risk you may install a firewall and only allow traffic to that port from loop back addresses(like 127.0.0.1).

;D

---

### Post by isaacj87 on 2007-05-30
is all of this necessary? I can't get sensors-applet to detect hddtemp unless i'm running it daemon with the ip address and the port # stuff.

---

### Post by araz on 2007-05-31
Hello,

I don't know another way :-k. if you manage another way post it, cause i would love to know it.

:D

---

