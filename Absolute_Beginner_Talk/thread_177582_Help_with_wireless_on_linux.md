---
title: "Help with wireless on linux"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by nidzoica on 2006-05-16
I'm using wireless card gigabyte aircruiser G and I don't know how to setup my internet connection. Where to find driver?

Just to say, I'm totaly beginner with linux ](*,)

---

### Post by evilgold on 2006-05-16
start by finding out what chipset your card uses. use the command "lspci" and post the line that has your wireless card. Try using this command "lspci | grep wireless"

For example heres mine:

```
root@lappy64:~# lspci | grep Wireless
0000:08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by nalmeth on 2006-05-16
Check my 'Wireless Help' signature link, and if it's too confusing, feel free to ask for elaboration on the confusing points.

---

