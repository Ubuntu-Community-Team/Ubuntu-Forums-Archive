---
title: "ssh: connect to host 192.168.0.35 port 22: Connection refused"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-18
Hi,

I try to connect to another computer within the local network via SSH, later I want to do that from outside the network.

When I enter: 
**ben@ben-desktop:~$ ssh ben2@192.168.0.35**

The error is produced:
[B]ssh: connect to host 192.168.0.35 port 22: Connection refused
[/B]

This is strange because in the router I also opened port 22, do I have to open the port 22 on the computer? If yes, how?

Thx

---

### Post by Hossie on 2008-01-18
When you connect from outside, you don't use your private IP, but the router's public IP.

---

### Post by Dr Small on 2008-01-18
Did you open port 22 on the system with the SSH server?

---

### Post by ben22 on 2008-01-18
ok, it seems the ssh server had not started properly,

thx, problem solved.

---

