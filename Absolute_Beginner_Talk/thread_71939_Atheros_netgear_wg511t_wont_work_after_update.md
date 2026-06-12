---
title: "Atheros netgear wg511t wont work after update"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by dewin on 2005-10-04
After updating the wg511t card wont work, trying to figure out how to reinstall the madwifi drivers, but dont know how, can anyone help or let me know what i can do to get it working again,
thanks i advance

Dewin

---

### Post by Mustard on 2005-10-04
This might be good start if you haven't seen it already.

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

help is also available in IRC.

---

### Post by loupy on 2005-10-04
I had the same problem with my D-Link G650 which is Atheros based.  I reinstalled the linux restricted module and rebooted and it worked.

In the synaptic package manager do a search for linux-restricted-modules-2.6.x.x and select the version that is for the kernel you are currently using.

you can find the kernel you are using by going to a terminal screen and typing in uname -a

---

