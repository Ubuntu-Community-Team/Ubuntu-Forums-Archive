---
title: "Installing ubuntu with an external CD Drive"
date: 2007-03-01
forum: Apple PPC Users
---

### Post by Bubbles7031995 on 2007-03-01
Hi, Im new to ubuntu. I have it installed on my desktop PC, and now I want to install it on my G3 Powerbook. The only problem is, I have an external CD drive.

Any suggestions on how I can install it?

---

### Post by PapaNerd on 2007-04-07
Can we presume that you are able to boot from the LiveCD when it is in the external drive (either without doing anything special or by hold down the "c" key as you power up)?

---

### Post by ZoiaGuyver on 2007-04-07
If the external drive is the only one connected it should do it with "c" being held on boot. If not try holding the "Option" key down before you hear the boot sound and it should force OF to give you a list of recognised boot devices, if the External is there you should be able to select it.

---

### Post by mylh on 2008-04-23
Hello, I have same problems insalling ubuntu from external CD drive. My device is connected to notbook through USB, menu with different options of loading and installing ubuntu is displayed, but when I select any menu item it tries to load something from CD and system halts i/e. nothing happens. What should I do? Thanks

---

### Post by avtolle on 2008-04-23
I'm no expert on this, but at one time, the external drive had to be a firewire drive in order to boot from it; no go on USB. Any Mac gurus out there who can set me straight on this?

---

### Post by stream303 on 2008-05-06
Once into the openfirmware, just issue this for a firewire CDrom / DVD drive:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

---

