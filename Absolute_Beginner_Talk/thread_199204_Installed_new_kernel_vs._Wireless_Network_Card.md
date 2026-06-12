---
title: "Installed new kernel vs. Wireless Network Card"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Imre Mehesz on 2006-06-18
hello,

i installed this new kernel version today 2.6.15-25-386. 

i went through all kind of things to set up my wireless under the old kernel (2.6.15-23-386)...

i don't know if i have to copy some set up files from the old kernel or I have to go through everything from the beginning again!?

thanks..
--
eMzMiM

---

### Post by robins_web on 2006-06-18
Launch synaptic and do a search for linux-wlan-ng:

**utilities for wireless prism2 cards**

linux-wlan-ng is a set of drivers and utilities that is intended to provide the full range of IEEE 802.11 MAC management capabilities for use in user-mode utilities and scripts.  The package currently supports the Intersil 802.11b Prism2, Prism2.5, and Prism3 reference designs for PCMCIA, PCI, and USB. Additionally, the package includes support for the PLX9052 based PCI to PCMCIA adapter with a few different PCMCIA cards.

The standard Ubuntu kernel already contains all necessary drivers. This package ships utilities and integration scripts to make above cards work seamlessly with the Ubuntu network infrastructure.

---

