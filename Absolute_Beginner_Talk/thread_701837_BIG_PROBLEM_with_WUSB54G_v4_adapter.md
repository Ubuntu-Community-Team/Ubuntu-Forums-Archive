---
title: "BIG PROBLEM with WUSB54G v4 adapter"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by pavlick on 2008-02-19
can anybody help me? I have the MOST puzzling problem! I have a dual-boot system, Windows XP and Ubuntu 7.10! Lately I have been using only my ubuntu but felt like playing a few windows games and I started to boot into my Win XP. at the Windows loading screen, my computer restarts. so i tried to start up in safe mode with networking, restarts as well, but I get a blue screen which says smth about rt2500usb.sys . i have not changed anything in my windows at all, is there anyway that using the rt2750 driver from this tutorial it would somehow affect the hardware in the usb adapter itself? how can i solve this?i used the " HOWTO: Linksys WUSB54G V4 in Gusty" post to configure my wireless on Ubuntu Gutsy but now my XP won't work with the adapter PLEASE IM IN DESPERATE NEED OF UR HELP!
ps, i have a wusb54g v4
thank you

---

### Post by dstew on 2008-02-20
> is there anyway that using the rt2750 driver from this tutorial it would somehow affect the hardware in the usb adapter itself?It is possible that the new driver updated the adapter firmware, so now it won't work with the older driver in Windows. You might try and update the Windows driver, if you can boot, and maybe get a wired internet connection. Sometimes you can put a new driver on a floppy, or USB  stick and get it into Windows that way. Check at th manufacturer's site.

I think your Windows will boot if you unplug the adapter.

---

### Post by pavlick on 2008-02-20
i did boot, i reinstalled the driver, and i got the same problem. i tried plugging the adapter into a different usb port. everything goes fine, the driver installs and the moment i try to connect to a network, i get a blue screen. and now my computer wont load with the usb adapter connected or unplugged. the usb adapter works fine in gutsy though. when i try to load windows in safe mode with the usb adapter unplugged, it just gets stuck on the mup.sys flie :( im lost

---

### Post by rustybronco on 2008-02-20
***edit***sorry I didn't see you tried it.

---

### Post by pavlick on 2008-02-20
> **rustybronco said:**
> see [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

how is this supposed to help me?

---

