---
title: "help with wlan"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by c hris on 2008-04-15
i am trying to install a driver for atheros wlan i have a disk with linux files on it but not the faintest idear what to do with it sensible answers please

---

### Post by jbrown96 on 2008-04-15
Throw that disk away. What is this Windows??? I'm just joking. 

There isn't any need for it though. If you were to use that disk you would have to compile the drivers from source every time you updated your kernel.
On the other hand, I like it when my computer does stuff like this for me.
 
Better solution: install the restricted modules. Note: you may also be able to install them via the Restricted Driver Manager (System--->Administration). If that doesn't work, open Synaptic and search for "Atheros" (no quotes). Install the option that matches your kernel version. You may also want the madwifi-tools. I'm not sure what it does but you might play around with it. A reboot may be required.

If you don't know your kernel version. Open a terminal and type
```
uname -r
```

hopefully network-manager will find your card. Make sure the card is on/plugged in and in a terminal run
iwconfig
This should display at least one device that has wireless extensions. I think it should be ath0 but it could also be wlan0 or ethX (where X is an integer).

---

