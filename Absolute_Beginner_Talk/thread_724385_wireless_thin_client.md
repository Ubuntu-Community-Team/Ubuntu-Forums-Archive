---
title: "wireless thin client?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by LRT on 2008-03-14
i'm kind of new at this thin client business. i have done my share of reading however and am in the process of setting up a thin client environment following this howto: [https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")

my question, is there a way to do this wireless???

---

### Post by MadMedis on 2008-03-14
I don't know too much about thin clients myself, but I'm pretty sure that network booting requires that the network adapter is PXE enabled, and wireless adapters are unable to provide PXE support.  FWIW  After a few quick yahoo searches I was unable to find any references to PXE working with wireless adapters.  If you can get PXE to work with a wireless adapter then you should be golden, but my understanding is that that isn't possible.

---

### Post by eriqjaffe on 2008-03-15
> **MadMedis said:**
> I don't know too much about thin clients myself, but I'm pretty sure that network booting requires that the network adapter is PXE enabled, and wireless adapters are unable to provide PXE support.  FWIW  After a few quick yahoo searches I was unable to find any references to PXE working with wireless adapters.  If you can get PXE to work with a wireless adapter then you should be golden, but my understanding is that that isn't possible.It should be possibe with a wireless bridge.

[http://dtmilano.blogspot.com/2006/08/pxe-wireless-booting.html](http://dtmilano.blogspot.com/2006/08/pxe-wireless-booting.html)

It's kind of an indrect form of PXE over 802.11, but it's better than nothing.

---

### Post by LRT on 2008-03-18
i'll look into that.. thanks!

---

