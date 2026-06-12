---
title: "Are the Nvidia drivers &quot;smart&quot;?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-09
I have a Geforce 64MB PCIE (can't remember what model off hand) that I will be replacing with a 6600 PCIE 512MB in a few days. Question is, can I just swap out the cards and the existing restricted driver (installed) will apply itself to the new card? Or is it a better idea to remove the driver, then re-install when I install the new card? Again, I am new (hence my reason for posting in this specific forum) and am used to Nvidia drivers covering a slew of cards (in Win32 that is). Just wondering if the same will apply here. Last thing I need is to swap cards and then not be able to boot into the GUI due to a driver issue. Any input is greatly appreciated of course. Thanks!

---

### Post by blackened on 2007-05-09
> **dpzektor said:**
> ...Last thing I need is to swap cards and then not be able to boot into the GUI due to a driver issue...

This is always a possibility, but is pretty easily dealt with most of the time. If it does happen, then just remember

```
sudo dpkg-reconfigure xserver-xorg
```

and you should be ok. Most (!) of the time accepting the defaults is enough to get you up and running with a gui, though I would suggest making use of the spacebar to select your desired resolution options when that part of the process comes up.

Per the driver issue, I would suggest disabling the restricted driver, install the new card, get back up and running (you might have to use the vesa drivers through the aforementioned reconfigure process), then re-enable the restricted drivers.

---

