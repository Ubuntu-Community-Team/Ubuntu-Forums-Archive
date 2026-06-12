---
title: "[SOLVED] ddclient question"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-13
I am running the configuration utility for ddclient and I was wondering what would be necessary to put in the "Interface used for dynamic DNS service" section. Any help is appreciated.

---

### Post by schwascore on 2007-06-13
this should be the network interface that serves as the connection to the Internet.  Usually it is eth0 (wired ethernet) or wlan0 (wireless).

To see all possible interfaces, open a terminal and run ifconfig.  That will list all active devices.

---

