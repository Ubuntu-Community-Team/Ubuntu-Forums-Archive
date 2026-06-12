---
title: "Wrong wifi net"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by 56seeker on 2007-08-02
Hi all;

Every time my laptop starts up it get holds of and connects to my neighbours wifi network.

I'd much rather it connected to my own! :)

How do I set a preferred default network while retaining the ability to connect to other wifi's where applicable, for instance cafe's and hotspots?

At the moment I'n running the default network manager applet ver 0.6.4

---

### Post by milosz.galazka on 2007-08-02
Hi,

Look at iwconfig man page, you can do it in that way (by network name)

iwconfig eth0 essid "My Network"

or register only to one access point (by mac address)

iwconfig eth0 ap 00:60:1D:01:23:45

---

