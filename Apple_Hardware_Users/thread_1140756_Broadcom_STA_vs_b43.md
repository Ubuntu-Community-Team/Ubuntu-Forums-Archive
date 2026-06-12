---
title: "Broadcom STA vs b43"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by Salohcin on 2009-04-27
I realise this could be an unexplored area of linux on mac support, but i was looking to give the b43 drivers another go, for wireless support on my mbp 4,1.

Currently am using the proprietary broadcom sta driver, and was just wondering if anyone had ventured down this path recently to see if they work any better.

---

### Post by pxwpxw on 2009-04-28
> **Salohcin said:**
> I realise this could be an unexplored area of linux on mac support, but i was looking to give the b43 drivers another go, for wireless support on my mbp 4,1.

Currently am using the proprietary broadcom sta driver, and was just wondering if anyone had ventured down this path recently to see if they work any better.

I am using the Broadcom STA driver for BCM4328 wirless chip, working well.
I dont think b43 supports the BCM4328, so it depends on what wireless chip you have.

```

pxw@mbp:~$ lspci -nn | grep Broad
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
pxw@mbp:~$ 

```

---

### Post by Salohcin on 2009-04-28
Bummer, you're right.  Don't know why i thought there was support for it, might've been on another system that i tried it.  Apparently they're looking at getting support for them (although who knows how soon).  Thanks though.

---

