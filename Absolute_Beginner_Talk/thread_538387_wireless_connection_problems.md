---
title: "wireless connection problems"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by gigab on 2007-08-29
I am new to Linux and I am trying to set up a wireless connection on my Ubuntu feisty fawn 7.04.
I have an ASUS WL107G wireless LAN PC card,  but I can not get it to work. When I plug it in it detects signals but can not connect to them. I have researched for days but could not find an answer, could you please help me out.

Thank you.

---

### Post by Kolfinna on 2007-08-29
post the listing of sudo iwlist wlan0 (or whatever your interface is)

---

### Post by kevdog on 2007-08-29
Must not have researched that hard...

Please post
lspci -nn
lshw -C network

---

