---
title: "How do iptables work?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-07-14
like most computer people, i like to know how things work.  I was wondering if someone could explain to me how iptables keep you secure and how they work.  More brief the better, i dont like to read alot :)

---

### Post by wolfen69 on 2007-07-14
iptables is just a built in firewall that will open/close ports as needed.

---

### Post by starcraft.man on 2007-07-14
> **wolfen69 said:**
> iptables is just a built in firewall that will open/close ports as needed.

Basically that's it. IPtables is just a firewall without the tray icon and GUI. On it's own its just a CLI program that is always running, and by default all your ports are closed.

If you want to really understand this stuff in depth, I direct you to security now. Episode 3 is for firewalls, episodes 25-29 deal with how the internet and LAN works, you kinda need that info to really understand how ports and the internet work and then how firewalls can stop it.
[URL="http://www.grc.com/securitynow.htm"]
Security Now[/URL] - All episodes are on this page.

---

### Post by adt41287 on 2007-07-14
awesome thanks.... any knowledge is good.....

---

### Post by starsky on 2007-07-14
hi there :)

Read this first [http://en.wikipedia.org/wiki/Netfilter](http://en.wikipedia.org/wiki/Netfilter)

then move on to [http://www.iptablesrocks.org/](http://www.iptablesrocks.org/)

Basically, iptables is a stateful firewall that uses kernel modules to make its rules. Those rules are used to identify traffic and filter them out as necessary. These rules are defined by users or system administrators.

If you want to dwell into the deep sea then there's always [www.netfilter.org](www.netfilter.org) :)

HTH

---

### Post by starsky on 2007-07-14
also note that it is pre-built into linux kernel version 2.6+.
Before that there was the world of ipchains.

---

