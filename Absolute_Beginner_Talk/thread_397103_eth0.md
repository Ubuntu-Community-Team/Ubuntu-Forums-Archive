---
title: "eth0"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-30
how i make sure that my if eth0 is in promiscuous mode ?? and what is the command 

to turn promiscuous mode off ???

---

### Post by dstew on 2007-03-30
ifconfig eth0 I think will list your configuration. ifconfig eth0 -promisc should turn promiscuous mode off. See the ifconfig manual (man ifconfig).

---

