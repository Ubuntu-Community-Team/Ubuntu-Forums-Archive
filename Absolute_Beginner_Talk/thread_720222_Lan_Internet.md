---
title: "Lan Internet"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by viju on 2008-03-10
I have iinstalled UBUNTU 7.1 Ultimate.I have Lan connection for internet.
I have configured conection by using Network manager.It detects eth0 lan card,Ping also shows bytes received and internet is on but i cannot open any website such as Google and Yahoo.I have 4 other Linux operating System and Windows XP.In all these OS I can connect to net.

---

### Post by prshah on 2008-03-10
> **viju said:**
> I have iinstalled UBUNTU 7.1 Ultimate.I have Lan connection for internet.
I have configured conection by using Network manager.It detects eth0 lan card,Ping also shows bytes received and internet is on but i cannot open any website such as Google and Yahoo.I have 4 other Linux operating System and Windows XP.In all these OS I can connect to net.

Post output of "cat /etc/resolv.conf", looks like your DNS settings are absent/invalid.

Cheers,
PRShah

---

### Post by zvacet on 2008-03-10
In DNS tab you will find address which you can delete and add your nameservers.After that go to the connection tab and tick your modem and window will pop up with message changing network interfaces(or something similar to that).When it is finish type in terminal   **pppoeconf**

---

### Post by viju on 2008-03-11
I added nameserver in /etc/resolv.conf file and internet started.Thanks for help.

---

