---
title: "Netgear wireless card won't work :("
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by MrHoneyBunny on 2007-06-20
Hi, I just installed Ubuntu for the first time and I'm having a problem with connecting to the internet.  This is the first time that I'm using Linux so I'm not familiar with any of the Linux commands yet and I feel very uncomfortable with the interface as of now.   Anyways, I have a Netgear Wireless USB 2.0 Adapter, model WPNT121 and for some reason, I can't even see a wireless option when I go to systems/network.  Ubuntu installed all of my other devices perfectly (even my Geforce graphics card) but the thing I consider most important to me, (the internet) won't work :(.  I was reading some topics online and it seems like there might be a way for me to use my Windows XP driver for it on Ubuntu?  Is anyone familiar with this?  I'd really appreciate any help on this because I do want to learn Linux.  Thanks

---

### Post by drivel on 2007-06-20
use command "lspci',can you find the infomation of your NetGear card?

---

### Post by drivel on 2007-06-20
Such as mine

$ lspci|grep Wireless
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by MrHoneyBunny on 2007-06-20
I don't even know where to go to type in commands yet :/...  Anyways, it's a usb device, not a card.  I should've been more specific in my toic title...sorry.

---

