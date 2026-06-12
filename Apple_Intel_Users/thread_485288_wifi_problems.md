---
title: "wifi problems"
date: 2007-06-26
forum: Apple Intel Users
---

### Post by AWerner32 on 2007-06-26
ok so i have a macbook first gen with the mad wifi driver and i was trying to patch that to use airodump for a little hobby because i was bored in the shop and wanted to see if i could crack the wifi in the store. things were going well and then shutdown when i left and when i booted back ath0 which is my wifi module wasnt on the ifconfig -a list. so i decided reload the module and```
 sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
so i reinstalled the madwifi drivers unpatched and tried it again; same error. Anybody know a fix?

---

### Post by david_edmundson on 2007-06-26
The output from dmesg would be helpful. Whilst you post that, a few helpful hints..

Have you tried turning it off and on again with a proper shutdown (it sounds corny but often it works)

When you reinstall the madwifi drivers make sure in "make install" you remove the old ones when it prompts you.

---

