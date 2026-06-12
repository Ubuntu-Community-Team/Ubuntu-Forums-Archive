---
title: "Need help on Dell wireless card"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Killamurk07 on 2008-01-28
Hey I have a Dell Latitude D610 and the wireless is not working.. Does anyone know/help where i can find a driver ...

---

### Post by amaroKer on 2008-01-28
You first need to find out what chipset your card has.  List your PCI devices, and look for a line that talks about "wireless", "802.11", or the like.  Try:
```
lspci | grep 802
```
or just
```
lspci
```
and look for the aforementioned keywords.

Post the output here.

---

