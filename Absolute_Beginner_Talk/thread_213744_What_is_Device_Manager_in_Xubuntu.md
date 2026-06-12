---
title: "What is Device Manager in Xubuntu?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-11
I'm using Xubuntu with Xfce.
I don't see a GUI front end for the device manager, so what is the CLI command to open it up?

Also, I need to check whether Xubuntu is working with my modem, but I do not have a dial-up service provider (nor even active phone lines in my house).  This is a year 1999 box, 440bx chipset, and a PCI modem card.  How can I check to see if Xubuntu can drive the PCI modem?

Thank you for answers to both questions!!

---

### Post by skale on 2006-07-11
For the first, not sure, try typing **lspci** to get all the PCI info. add -v and -vv to get progressively more information. type **lshw** if you want the whole device manager information. (or I think, I never knew there was a device manager in ubuntu, I've just seen it in windows)Not sure what to do about the modem, as the best way to see if it works is to use it, but post the section in lspci -vv about it and someone might know what to do.

---

### Post by Kilz on 2006-07-11
> **Susan.Desanco said:**
> I'm using Xubuntu with Xfce.
I don't see a GUI front end for the device manager, so what is the CLI command to open it up?

Also, I need to check whether Xubuntu is working with my modem, but I do not have a dial-up service provider (nor even active phone lines in my house).  This is a year 1999 box, 440bx chipset, and a PCI modem card.  How can I check to see if Xubuntu can drive the PCI modem?

Thank you for answers to both questions!!
Try 
```
hal-device-manager
```

---

### Post by Susan.Desanco on 2006-07-11
Thanks to you both!  While the advice from Kilz did not want to work, the advice from skale did indeed do the trick.  I appreciate both of your help.

---

