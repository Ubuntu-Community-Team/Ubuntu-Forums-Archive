---
title: "Here we go again with the kernel panics..."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-06-03
When I thought I had Feisty working right, after downgrading to Edgy (fresh installs) then going back to Feisty because I figured out the problem with Vendetta Online, here we go again with the locked blank screen and the caps lock flashing. I have read that this is a kernel panic. It doesn't happen in Edgy.

Laptop
HPDV6000
1024 ddr2 ram
120 gig hd
Feisty Fawn 7.04

Is this dangerous?? It happened for the first time since I installed Feisty when I left the laptop downloading a file for like 2 hours. This is when it happened before, too.

Thanks for any help...:(

---

### Post by mystman on 2007-06-03
If it only happens in Feisty it's probably a software incompatibility with your hardware, or maybe a broken package from the upgrade.

---

### Post by Ripfox on 2007-06-03
There was no upgrade, I always do a clean install.

---

### Post by tgalati4 on 2007-06-03
Could be the network card is overheating causing the system bus to lockup.  Any messages in dmesg or in /var/log?

Linux expects perfect network hardware communication.  I had kernel panics with an overheating/intermittent wireless card.  Replacing the card took care of the problem.

---

