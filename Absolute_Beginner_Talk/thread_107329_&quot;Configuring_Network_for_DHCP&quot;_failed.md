---
title: "&quot;Configuring Network for DHCP&quot; failed"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by anoncompboy on 2005-12-22
When installing ubuntu, it fails the "Configuring Network for DHCP."

My PC connects to the internet either through wired ethernet or with my PCI wireless card. Most of the time I choose to not be connected to the internet at all, and hook up to another PC via a wired crossover cable.

What do I do? For now, can I choose "do not configure network now" and configure it later?

---

### Post by darth_vector on 2005-12-22
yes. this will only work if you have a DHCP server running. most modern home routers have the option of enabling DHCP.

the alternative is to set up the network manually and give your machine a static ip address.

---

### Post by anoncompboy on 2005-12-22
thanks, i chose "configure it later."

In windows XP, I had to choose "automatically assign an IP" when connecting to a WLAN or LAN. How do I do this in ubuntu?

---

### Post by darth_vector on 2005-12-22
the auto assign in windows XP uses DHCP. it may be that your wired network card is unplugged and your wireless card needs to be setup...

---

