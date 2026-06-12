---
title: "Can't connect to internet using DesktopBSD Live DVD"
date: 2008-08-03
forum: BSD
---

### Post by Comhra on 2008-08-03
Well, I'd like to dual boot _but_ I have a Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13) card and they just don't seem to work in BSD.

I'm not the only one with this problem, maybe one or two here have had it.  Is there a workaround?

Makes me appreciate Ubuntu all the more.

Everything just works.

:):):)

---

### Post by Comhra on 2008-08-03
I'm just a sucker for *nix.

:lolflag:

---

### Post by Comhra on 2008-08-03
Tell you what: it's given me a new perspective on those unfortunate people who's hardware doesn't support  Ubuntu.

I've spent a frustrating night and got nowhere.

Still I'm not blaming BSD.

I've tried Dragonfly (not for noobies), PCBSD and now DesktopBSD all with the same result, no net connection.

At least I know now that it's the Ethernet card so my time wasn't completely wasted.

---

### Post by mips on 2008-08-03
> **Comhra said:**
>  Is there a workaround?


Yes. I'll get there later.

From what I understand the [msk(4)]("http://www.freebsd.org/cgi/man.cgi?query=msk&apropos=0&sektion=4&manpath=FreeBSD+6.3-stable&format=html") driver should support your card.

I have also heard of people using the FreeBSD driver from Marvell, [http://www.marvell.com/drivers/driverDisplay.do?driverId=139](http://www.marvell.com/drivers/driverDisplay.do?driverId=139)

Now for the simple workaround if none of the above works. Install ndiswrapper & use the windows driver.

---

### Post by Comhra on 2008-08-03
I'll try those, thanks Mips.

---

