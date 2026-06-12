---
title: "i want to see my apache web server from the net how do i turn ubuntu firewalls off"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2008-03-26
hello,...i want to turn all the firewalls in ubuntu 7.10 server edition off..how can i do it??

---

### Post by Bachstelze on 2008-03-26
It is **definitely not** a firewall problem.

Please be more precise about how your network is setup (e.g. if you have a router, make sure port 80 is forwarded).

---

### Post by Oldsoldier2003 on 2008-03-26
> **psychobeauty said:**
> hello,...i want to turn all the firewalls in ubuntu 7.10 server edition off..how can i do it??

unless you configured iptables the "firewall" isn't actually doing anything. if you have made some rules you can run iptables -F to flush the rules.

---

