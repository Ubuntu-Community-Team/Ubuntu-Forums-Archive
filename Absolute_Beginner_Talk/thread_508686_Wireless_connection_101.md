---
title: "Wireless connection 101"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by cbivins on 2007-07-24
i'm new to ubuntu and i just loaded Feisty Fawn. My ethernet connection is working fine, but when i try to connect to a wireless connection, i am completely lost. Can some nice person walk me through the process step by step. Keep in mind that i'm a newbie, so keep it dumbed down if you can. Thanx in advance.

---

### Post by FleetAdmiral74 on 2007-07-24
Well first of all, can you provide some info on stuff like your wireless card brand and model, and the router? That should be helpfull

---

### Post by cbivins on 2007-07-24
I guess i should have done my research first and then asked. Thanks any way though.

---

### Post by ugm6hr on 2007-07-24
The info is easily available from within Ubuntu.

In Terminal (find it in Menu), just type:
```
lspci
```
Look for Network / Ethernet Controller information.

The type of wireless router security you use is also necessary - because it is best to try and connect with security (e.g. WEP/WPA) first, then to sort security afterwards.

Other useful info contained within the following, although this is not necessary to begin with:
```
iwconfig
ifconfig
lshw
```

---

