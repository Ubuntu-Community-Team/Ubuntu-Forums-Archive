---
title: "internet on gutsy,tiger and xp"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2008-01-04
loading time from my home page(yahoo) to craigslist (after clearing cache) on a dual boot machine

gutsy= 17 seconds
xp=7 seconds

mac os tiger=11 seconds  (imac dv)

all are hard wired to my verizon dsl router

my laptop c600 with a belkin wireless card xp =4 seconds

why is gutsy the slowest?

iam using firefox for all

---

### Post by RomeReactor on 2008-01-04
Hi. Maybe disabling IPv6 in Firefox can help; open a new tab and in the address bar write:
```
about:config
```
then in the filter write **ipv6**; double click on the result (network.dns.disableIPv6) to set it to "True". Then restart Firefox.

---

