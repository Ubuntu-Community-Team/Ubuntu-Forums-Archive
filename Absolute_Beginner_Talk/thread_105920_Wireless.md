---
title: "Wireless"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-19
I'm just wondering, this is a post about wireless that i saw in a forum, would it work in similar way in Ubuntu?

> IEEE 802.11g is the standard your card is using, not the brand and model.

Anyways, you might need to:
1) install the "ndiswrapper" package form the control center
(this will allow you to use the windows drivers supplied on cd for your card)
2) mount your windows drivers cd and find the directory where the xxxx.inf file is
located
3) in a shell, go to that directory as root.
4) type ndiswrapper -i xxxx.inf (this will copy the driver files)
5) type ndswrapper -l (this will list teh installed drivers)
6) if you see your driver listed, type ndiswrapper -m (this will update your confiiguration
files)

you can the do several things:
1) type "modprobe ndiswrapper" to load the driver
2) type "iwconfig" and see if you now see a WLAN0 item

3) in xandros control center, go to your wireless settings and tell it to youse your
ndiswrapper as a driver (and al your network related settings) so it will be activated
on boot-up


This might not be 100% complete, but should put you on track

---

### Post by Kyral on 2005-12-19
If your wireless card shows up when you do "ifconfig" then it works

If not you need NDiswrapper, which is on the CD

---

