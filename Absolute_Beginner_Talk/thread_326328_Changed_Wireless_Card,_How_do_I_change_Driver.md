---
title: "Changed Wireless Card, How do I change Driver?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by FingerPie on 2006-12-27
As the title states, I replaced an Intel 2200 internal (miniPCI) card with a Compex card that uses a different chipset (Atheros).

If I boot the laptop with a USB distro (like Backtrack or SLAX), the atheros chipset is identified and madwifi is used to assign the device as ath0.  It works great.

I had installed Ubuntu with the intel card in.  I am pretty sure the old driver is being used, only a handful of networks can be seen and I can't connect to any of them.

(1)  How do I completely uninstall the existing driver for the wireless card?  Where is it?

(2)  I would like to use madwifi to run the card, do I DL and compile the driver from their site or is there a way to make Ubuntu "re-detect" and install a wireless driver for my new card?

FP

---

### Post by FingerPie on 2006-12-27
Wow,

I have been spending the day looking into this, even removing an existing madwifi install can be a pain... I can't find anything about removing the Intel driver.  I think I'm looking at a new custom install of Ubuntu, then manually installing madwifi-ng.

---

