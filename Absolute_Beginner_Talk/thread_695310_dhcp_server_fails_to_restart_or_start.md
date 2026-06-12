---
title: "dhcp server fails to restart or start"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2008-02-12
dhcp3-server fail to restart

---

### Post by brettg on 2008-02-12
Firstly, you need to provide much more detail than that if you want help, but I will do my best.

You can either check the system log with cat /var/log/syslog | grep dhcp to see where in your dhcp.conf file the error lies (your problem is a badly configured dhcp.conf I expect)

Alternatively, I've found that dnsmasq is an excellent alternative that will give you dhcp and dns caching servers which is super easy to set up. If you are setting up a home gateway then you could do worse than to use dnsmasq.

---

