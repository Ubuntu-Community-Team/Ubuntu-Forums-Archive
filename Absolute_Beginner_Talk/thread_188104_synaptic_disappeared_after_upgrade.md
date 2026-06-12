---
title: "synaptic disappeared after upgrade"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by x96riley3 on 2006-06-03
I used synaptic to upgrade to 6.06 and now my synaptic package manager is gone.

system->administration-> not there

root@st00ctrl:~# apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by johnc4510 on 2006-06-03
Looks like you just lost it from your menu. To verify this open the terminal and enter: sudo synaptic
If it starts, you just need to add it to a panel or to your drop down menu

---

