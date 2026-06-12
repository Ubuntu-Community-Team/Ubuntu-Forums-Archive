---
title: "Boot without Ethernet cable?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by i4ni on 2005-12-07
When I boot from the Grub menu (I dual boot w/ Win2k), the gui will only load if my ethernet cable is plugged in (I used it, rather than my wireless card, during the install; I don't have a working CD drive, so did it via Windows and over the network). Ubuntu stops loading until the cable is plugged, even though I disable it (in favor of the wireless card) when the gui is up.

Can I somehow change my setup process to either look for the wireless card instead; or, since it doesn't need an Internet connection during boot up, change it so that it skips this step entirely?

Thanks all for your advice and assistance.

---

### Post by ape on 2005-12-07
check out the ifplugd package.

---

