---
title: "Internal ? External Wireless?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-03-31
I finally got a Broadcom 4311 internal wireless card working on a Lenovo laptop using ndiswrapper. I also have a Netgear WG511T. For reasons only a masochist would understand, I'd like to be able to use either one. 

If I plug in the WG511T card, it is recognized (06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)) but doesn't seem to work, even when I boot with the internal radio turned off.

Is it posssible to have both the internal radio and the external card both configured so that either will work depending on whether I have the external card inserted?  If so, how do I go about it?  Can you have ndiswrapper working on both the internal and external cards in the same setup?

If someone who can't get ANY wireless to work is just shaking their head at my greed please forgive me!

---

### Post by GrannyBat on 2007-04-02
__

Hi, I am a newbie as well and I have a Lenovo 3000 C100 which I was unable to get either the Internal wireless card or my Belkin Ralink chip pcmcia card to work while I used Dapper.  I am told it is possible to get the internal card working with ndiswrapper and it is possible to get a pcmcia card to work if you disable the internal wireless adapter.  I don't know if you can keep both enabled at the same time.  I have upgraded to Edgy and by following the instructions posted by nickm re Broadcom cards I now have a fully working Broadcom card with wap encryption enabled without using ndiswrapper.  Try entering [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) to get the details.  (I am sure there is a shorter way of finding this but I don't yet know what it is.)  I want to try to get my Belkin card working as well and I am told that Belkin and Netgear share some drivers so if I get this to work I will let you know.  If not I will tell you what did not work!
Best wishes.

---

### Post by drs305 on 2007-04-03
> **GrannyBat said:**
> __
I am told that Belkin and Netgear share some drivers so if I get this to work I will let you know.  If not I will tell you what did not work!
Best wishes.

Ditto for me. If I find an answer on using an external card while preserving the opportunity to use the internal card at other times I'll post it here. 

I used ndiswrapper to get my internal wireless to work but I'll check out the link you posted.

---

