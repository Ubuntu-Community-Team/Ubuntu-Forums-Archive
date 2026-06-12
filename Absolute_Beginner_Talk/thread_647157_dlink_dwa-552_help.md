---
title: "dlink dwa-552 help"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-12-22
Hey all,

I just built a new computer from scratch, and installed Ubuntu on it!

I have a D-Link DWA-552 card, from which I can tell is running an atheros chipset.
I am trying to get it to work in gutsy.
After installing, it shows up in network-manager, but when i click on it and try to connect to my network, the computer freezes.

I uninstalled network manager and everything seems to work, except I cant connect to my network.

If i do an ```
iwlist scan
``` my network comes up.  
```
sudo ifup wlan0
``` doesn't recognize the interface
```
sudo dhclient wlan0
``` says discovering a couple times and then says no devices in persistant database... sleeping or something to that extent.

Any help connecting to my wireless network?  (WPA)

---

### Post by sc30317 on 2007-12-22
no one?  please help, this is my only way of getting to the internet on my desktop without moving the entire computer

---

### Post by sc30317 on 2007-12-22
pretty please?!?!?

---

### Post by sc30317 on 2007-12-23
come on, someone's gotta be able to help

---

### Post by sc30317 on 2007-12-23
da mot i need some help people

---

### Post by syxbit on 2007-12-26
some advice
check here before you buy hardware.
i had an old Linksys, that i spent hour with ndiswrapper on
then my new desktop had built in railink, that had constant disconnects
i just bought a dlink with atheros the other day, and it's perfect.
$28 after rebate. it just works! no effort. i know it sucks to buy new hardware, but seriously. how much is your time worth. for $28 you can have no more wifi problems
i got the dlink WDA-2320

---

