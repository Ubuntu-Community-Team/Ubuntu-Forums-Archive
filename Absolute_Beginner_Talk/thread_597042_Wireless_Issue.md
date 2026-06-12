---
title: "Wireless Issue"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by tw0shoes on 2007-10-30
So my wireless was working, then I reboot and it stops. Its a broadcom 43xx, i have the firmware, and drivers. Any hints?

---

### Post by paul.matthijsse on 2007-10-30
try re-activating it in Network Manager...

---

### Post by PartisanEntity on 2007-10-30
also try:

```
ndiswrapper -l
```

and see what it says

---

### Post by tw0shoes on 2007-10-30
Sorry. Where is Network Manager? under Admin I can find Network and Network Tools, but i see nothing about a wireless card in there.

---

### Post by tw0shoes on 2007-10-30
says: 
Error: no ndiswrapper utils found!

after I installed it....

---

### Post by PartisanEntity on 2007-10-30
Open Synaptic and look for ndiswrapper, you will find an entry for ndiswrapper-utils install it too.

---

### Post by tw0shoes on 2007-10-30
ndiswrapper -l didn't return anything...

---

### Post by tw0shoes on 2007-10-30
so what now?

---

### Post by tw0shoes on 2007-10-30
help!

---

### Post by paul.matthijsse on 2007-10-30
type in a terminal:
$ lspci

any broadcom stuff listed there?

---

### Post by tw0shoes on 2007-10-30
~$ lspci | grep Network
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

So yes.

---

### Post by paul.matthijsse on 2007-10-31
Hello, try to re-install this driver, see this how-to:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

you need to do step 1, 2b and 3. Worked for me (with a 4318 )

---

