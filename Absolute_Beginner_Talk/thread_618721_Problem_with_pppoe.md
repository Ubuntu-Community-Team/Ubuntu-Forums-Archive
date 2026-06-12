---
title: "Problem with pppoe"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by eimor on 2007-11-20
I have a problem with pppoe. It used to work fine, until last week i had to get some information from my laptop using the lancard. I disconnected the adsl modem and forgot to plug it in again. Then i swithched off my pc and went away. But after that my brother turned on the pc and booted in ubuntu, he tried to open firefox but he couldnt connect (of course, if he wasnt connected to the modem) but then he plugged it in and called pppoeconf from terminal (he saw me doing that when i configured it for the first time) and did all the steps again. Now i think i have to process or something running redundant and those things are blocking each other. How could i get to know if there are "two connections" blocking each other? Does this issue have something to do with the fact that sometines i cant connect and i have to reboot?

---

### Post by OffAxis on 2007-11-20
try
```
pppoe-discovery
```


**/etc/ppp/peers/provider** is your default configuration file; it may have been modified or erased.

---

