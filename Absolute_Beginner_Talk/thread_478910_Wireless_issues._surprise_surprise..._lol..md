---
title: "Wireless issues. surprise surprise... lol."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by The Persian on 2007-06-19
Ok so i just installed the linux-wlan-ng package for my prism 2 pci chipset and i actually get an ip address and i have a mac address but i'm not getting a subnet or any of the other stuff i need.
when i type in ifconfig it says my wlan is up and it is seeing the wnetwork but something isn't doin' it's job :( . any ideas ?  thanks in advance for any help.

---

### Post by st33med on 2007-06-19
What's your wireless card? If you don't know, go to Terminal and type the following:
```
lspci
```

---

### Post by The Persian on 2007-06-19
Intersil Corporation Prism 2.5 Wavelan chipset (rev. 01)

---

### Post by The Persian on 2007-06-19
I take it this chipset is a pain in the ***... lol

---

### Post by st33med on 2007-06-19
Well, when I looked it up it said the driver was already preinstalled in the Linux kernel. So... I don't know...

try 'iwlist scanning'

---

### Post by jimrz on 2007-06-19
> **st33med said:**
> Well, when I looked it up it said the driver was already preinstalled in the Linux kernel. So... I don't know...

try 'iwlist scanning'

try checking in networking to make sure that your dns server info is correct. have had this happen in the past and changing the server info resolved the prob.

---

