---
title: "Ubuntu is about to make me look stupid if i dont fix this"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-10-06
Im putting it on a firends acer and i followed instructions on how to get the wireless to be recognized, and now that i try to connect to a wep2 network the thing freezes, wep works fine and the ethernet too but wep2 freezes the whole system.  wtf?

---

### Post by ronocdh on 2007-10-06
> **Hmarroqu said:**
> Im putting it on a firends acer and i followed instructions on how to get the wireless to be recognized, and now that i try to connect to a wep2 network the thing freezes, wep works fine and the ethernet too but wep2 freezes the whole system.  wtf?
This is extremely dependent on the wireless chipset and the method you've used to configure the card. For example, MadWifi is a very popular open source option for many cards, but easily just as many users are still forced to use something like ndiswrapper, which just applies a Windows driver package to your hardware in Linux.

WEP2 is often problematic with chipsets which are not fully supported. WAP can be even worse. It is a big problem, and this is why all supports of free software are encouraged to be very prudent in their selection of hardware to purchase, as the more chipsets without free drivers and firmware that are purchased, the more their manufacturers will be assured that users are satisfied with that level of support.

---

### Post by Catsworth on 2007-10-06
This doesn't necessarily help you, but you really shouldn't be using WEP if you can help it.

WEP (given the right circumstances - 40k packets, and about 30 seconds) can be cracked *very* easily.

Move to WPA if you can.

---

### Post by Travisher on 2007-10-06
download Wicd and replace the NetworkManger , it just works most of the time.
3rd party product
deb: [http://wicd.longren.org](http://wicd.longren.org) fiesty extras in your synaptic package manager

---

