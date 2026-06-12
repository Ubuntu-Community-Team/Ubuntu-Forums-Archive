---
title: "VMPlayer and Ubuntu Server 7.10"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by cwhitmore on 2008-02-28
I installed Server 7.10 insid vmplayer. I've logged in and noticed that the IP address assigned is 192.168.106.130, but our subnet is 192.168.100.xxx. 
When I try to ping an outside domain I get the IP address, but it's not able to ping the address. I'm assuming this is a routing issue, but is it a VMWare issue or Ubuntu?

---

### Post by brettg on 2008-02-28
The IP address you are referring to, is that in the guest or the host?

---

### Post by cwhitmore on 2008-02-29
It's the guest IP address. (Ubuntu server is the Guest and Vista is the host). The IP on the host is 192.168.100.46

---

### Post by cwhitmore on 2008-02-29
I started my other guest OS which is WinXP Pro and it also uses the submet 192.168.106.xxx, but it works fine. I'm able to get to websites with it.
Has anyone else had problems with Ubuntu Server and VMPlayer?
The IP address that's coming up with is 192.168.106.130. When I ping a domain outside of our network it returns the correct IP address, but it's not able to reach it.
Any ideas?

---

