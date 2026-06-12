---
title: "kismet touble"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by weezy8802 on 2008-03-17
ok i read several threads from different sites and cant find any help yet. i am trying to configure my kismet.conf file and it tells me that i cant save the file. i have changed permissions and tried multiple things. any help is appreciated.

---

### Post by taurus on 2008-03-17
Instead of changing permissions and screwing your system up big time, edit it with sudo/gksudo.

```
gksudo gedit kismet.conf
```

---

### Post by weezy8802 on 2008-03-17
ok i got that now i get this error.

WARNING:  Could not get mode of vap ath0::wifi0, skipping
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.

---

