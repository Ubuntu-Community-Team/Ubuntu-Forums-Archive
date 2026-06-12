---
title: "internet device switching."
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-10-03
When i use wireless and switch to wired my signal never sends. it only receives and idle. But when i switch to wired and restart, it fixes. any way to fix this so i dont have to restart everytime?

thanks!

---

### Post by bulldog on 2006-10-03
Activate the proper ethernet device in your Administration--Network.

There should be more then one I guess,probably eth0 and eth1,and one of them is active.

---

### Post by n0dl on 2006-10-03
Have you tried stopping your wireless device (ath0, wlan0, eth1, etc) then running sudo dhclient eth0? (or whatever your wired ethernet card is)

---

