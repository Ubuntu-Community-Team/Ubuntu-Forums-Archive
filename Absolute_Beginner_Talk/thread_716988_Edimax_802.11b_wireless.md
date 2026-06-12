---
title: "Edimax 802.11b wireless"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-06
Hi,

I'm running damn small linux and I cant use the forum (its not working for me) I thought being Debian someone could help me on this forum please.

I've just connected a EDIMAX 802.11b to my laptop.

Could anyone please give me a step by step guide as to how I start getting it up and running - bearing in mind I'm a newbie!

Also what additional software do I need to begin - anyone with a knowledge of DSL would be greatly appreciated.

Thanks

---

### Post by kwacka on 2008-03-06
You might get more information from DSL forums - it is based on Knoppix, which was based on Debian. DSL do state that they are NOT Debian.

If you go to the Edimax site they do provide Linux drivers for some of their cards.

It might be that

---

### Post by the beak on 2008-03-06
I've logged onto that forum but it only allows you to read post, not post!!

---

### Post by neurostu on 2008-03-06
have you tried installing the driver from the Edimax site?

---

### Post by the beak on 2008-03-06
There doesnt seem to be any support!

---

### Post by anewguy on 2008-03-06
Did the wireless come with a Windows install disk?  Are Windows drivers available at the Edimax site?  If so, we might be able to get you running with ndiswrapper.

Please let us know if you have/can get the Windows driver. :)

---

### Post by kwacka on 2008-03-08
> **the beak said:**
> I've logged onto that forum but it only allows you to read post, not post!!

I went to the DSL site & went to the networking section:

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=SF;f=7](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=SF;f=7)

under the sticky "working wireless cards" is a link to the wiki: 
[http://damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards](http://damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards)

a link here goes to: [http://linux-wless.passys.nl/index.php](http://linux-wless.passys.nl/index.php)

Ideally you need to find out the chipset used by the card, if its usb try typing 'lsusb' in a terminal, if its PCMCIA or Cardbus type 'cardctl' and take it from there.

---

