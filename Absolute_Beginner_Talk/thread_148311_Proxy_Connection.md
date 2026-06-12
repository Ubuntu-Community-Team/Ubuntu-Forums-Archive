---
title: "Proxy Connection"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-21
Im connected to the internet through a sucky proxy connection that blocks most programs, browsers can get the internet connection when a Auto configuration URL is entered but most other programs dont work. I dont even think the terminal is seeing the internet connection and this could be why none of my packages are installing, is there a simple test i can do to check this??

Thanks very much!

---

### Post by dcstar on 2006-03-22
[QUOTE=tommy1987]Im connected to the internet through a sucky proxy connection that blocks most programs, browsers can get the internet connection when a Auto configuration URL is entered but most other programs dont work. I dont even think the terminal is seeing the internet connection and this could be why none of my packages are installing, is there a simple test i can do to check this??

Thanks very much![/QUOTE]
traceroute <ip address or name>

Synaptic has a specific place for you to manually enter your proxy information, once you do that Synaptic should be able to download packages.

---

### Post by public_void on 2006-03-22
See this [post](http://www.ubuntuforums.org/showthread.php?t=123984&highlight=proxy) on editting apt.conf with proxy details to get apt-get working.

---

