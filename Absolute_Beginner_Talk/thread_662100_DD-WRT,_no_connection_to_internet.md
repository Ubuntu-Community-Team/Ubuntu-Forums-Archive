---
title: "DD-WRT, no connection to internet"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Daghita on 2008-01-08
Decided to switch up routers and go with my Linksys WRT54G ver. 6 running DD-WRT Micro ver. 23 sp 2. I have one computer (win2k) connected to the WAN and receives internet signal just fine. I have another computer (winXP) connecting to it wirelessly and receives internet signal just fine.

But, I go to try and connect my laptop using madwifi drivers and it'll connect to the router just fine, although you can't connect to the internet. I know the laptop receives signal just fine because I can switch it back up to the other router wirelessly and it connects just fine.

It seems that Ubuntu says "nope" to DD-WRT. Something about my settings on Ubuntu?

***SOLVED*** One of the major difference between the other computers and my laptop...is MOBLOCK! Disabling Moblock restored the access. Now I just have to adjust the settings in Moblock so everyone plays happy.

---

