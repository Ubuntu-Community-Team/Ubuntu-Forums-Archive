---
title: "need help with gateway 7422"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ryansmith1234 on 2008-03-08
I can't figure out how to get the drivers for my ethernet card or the wifi card.  I also don't know how to install.  I have read old forums for hours and tried to follow the steps but I can't get them to work.  Any help would be greatly appreciated.  Thank you.

Ethernet Card:  Via Technologies VT6102 RHINE-II
WIFI Card:  Broadcom bcm4306

---

### Post by handydan918 on 2008-03-08
It may be helpful to post the output of ```
lspci | grep -i net
```
as well as ```
lsmod
```

---

