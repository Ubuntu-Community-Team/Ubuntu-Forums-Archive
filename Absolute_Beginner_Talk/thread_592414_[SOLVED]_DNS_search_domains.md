---
title: "[SOLVED] DNS search domains"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jmeyer on 2007-10-26
[SIZE="2"]I will add multiple search domains in DNS within the System>Administration>Network dialog box, but every so often it removes the ones I add.  I have to RDP using the IP address but would like to be able to keep the added search domains permanently.  I am set up on our network with a DHCP reservation.  [/SIZE]

---

### Post by sneezymelon on 2007-10-26
I was having the same problem. Open DNS provided for this problem. You can use the same method with your DNS servers. Here's the link- [https://www.opendns.com/start?device=ubuntu]("https://www.opendns.com/start?device=ubuntu")
It involves editing your resolv.conf.auto instead of your resolv.conf

---

