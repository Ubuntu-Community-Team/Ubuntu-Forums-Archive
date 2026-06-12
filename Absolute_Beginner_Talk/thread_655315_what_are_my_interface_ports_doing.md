---
title: "what are my interface ports doing?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by ubiubi on 2008-01-01
How do I check to see if interface port 1213 is currently in use.

---

### Post by blueridgedog on 2008-01-01
Man tcpdump for more information.

Try:

```
sudo tcpdump -i eth0 port 1213
```

---

### Post by ubiubi on 2008-01-01
mark@mark-desktop:~$ sudo tcpdump -i etho port 1213
[sudo] password for mark:
tcpdump: SIOCGIFHWADDR: No such device
mark@mark-desktop:~$ 

Any suggestions. my apollon program refuses to connrct and when I tpye giftd I get the c'check interface ports 1213 request

---

### Post by blueridgedog on 2008-01-01
That is eth0 E T H ZERO.

Assuming that you want to use your first interface.

---

