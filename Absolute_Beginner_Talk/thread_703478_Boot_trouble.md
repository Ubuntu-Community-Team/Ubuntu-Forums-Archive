---
title: "Boot trouble"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Johnny.P on 2008-02-21
Ubuntu was working fine until I installed a new graphics card (ATI X1650) - its parting shot tells me- no resume image - and then all goes blank. Any ideas much appreciated.

---

### Post by dstew on 2008-02-21
If you have installed a new graphics card, you need to re-configure the xserver in order to get your desktop back. After you boot, when the blank screen appears, type the key combination ctrl-alt-F1. That should get you a command line screen. At the command line, enter ```
sudo dpkg-reconfigure xserver-xorg
```Answer the questions the best you can. Choose the ati or vesa driver for the display. After you have finished with the reconfiguration, enter```
startx
```to re-start your xserver. Then, go to the Restricted Drivers Manager in your System --> Administration menu, and see if you can install a better driver for your card.

---

### Post by Johnny.P on 2008-02-22
Thanks for your reply- I feel i've made progress but still no desktop. I have the following warning:-

(WW)RADEON : No matching device section for instance (BUS ID PCI:1:0:1) found (EE) No devices detected.

Maybe I have set the wrong bus address althoughth I did use LSPCI- would it be a PCI Bus address for an AGP interface?
thanks

---

### Post by dstew on 2008-02-22
> (WW)RADEON : No matching device section for instance (BUS ID PCI:1:0:1) found (EE) No devices detected.This line comes from the xserver, and it means that it was unable to find a device entry for your graphics card in its xorg.conf file. Did you reconfigure the xserver as I previously recommended? If so, there should be a device entry.

---

### Post by Johnny.P on 2008-02-23
My desktop has re appeared- I followed your instructions and chose the vesa option-now to sort my driver. Thanks for the help.

---

