---
title: "Squid blocking...?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by bushtor on 2006-02-16
Hi,

Yesterday I installed firestarter and could browse the internet with computers connected to the ubuntu computer's LAN NIC.  In the evening I stopped firestarter and this morning I started it again.  But this morning I could not browse the internet neither from the ubuntu computer nor from the client computers.  I have not changed anything to my knowledge.  I can ping the internet (name servers etc) from the client computers bur I have no www access.

Can squid be blocking something or what should I look for to have port 80 traffic running again?

Thanks for hints on this issue

bushtor

---

### Post by piedamaro on 2006-02-16
Try to check your connection without firestarter, then re-enable connection sharing   on firestarter and try again.
Squid is a proxy server and it's unrelated to firestarter which is a gui for iptables.

---

