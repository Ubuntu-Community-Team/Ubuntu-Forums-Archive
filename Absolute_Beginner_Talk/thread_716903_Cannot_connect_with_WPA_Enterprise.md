---
title: "Cannot connect with WPA Enterprise"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-06
I've tried messing around with my network settings, even just plugging in a wire to the wall, but for the life of me I cannot get any form of internet connection to work on my laptop. 

The wireless on campus requires WPA Enterprise (not currently available through Network Manager in GNOME), TKIP data encryption (again, I don't see an option anywhere for it), and PEAP, enabling network access control using IEE802.1X. I cannot find the options for any of this anywhere in Ubuntu Gutsy. 

 I can get internet to work through the dual boot part of XP Pro that I have on my laptop, but I'd much rather use Ubuntu if I can. I've tried the one walkthrough with editing the network interfaces file but got lost in it. Um, help?

---

### Post by jeffus_il on 2008-03-06
What wireless card do you have?

---

### Post by spacefreak86 on 2008-03-06
Broadcom Netlink Gigabet Ethernet for the wired and Intel Pro/Wireless 3945ABG Network Connection for wireless.

---

### Post by jeffus_il on 2008-03-07
What is the name of the driver module used for networking?

Someone solved problems with card by moving from NetworkManager to Wicd:
[http://ubuntuforums.org/showthread.php?t=688253&highlight=3945ABG](http://ubuntuforums.org/showthread.php?t=688253&highlight=3945ABG)
It seems like the intel driver does support wpa.

---

