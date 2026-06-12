---
title: "Network card issues with HP Pavilion"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Phuzzy_one on 2008-04-07
Just got a new system and the network card does no work when booting to a live cd, the card lists as a realtek RTL8168c/8111c Family pci-e gigibit in windows, any idea on how to get it to work?

---

### Post by jbrown96 on 2008-04-07
Couple of things to start with:
```
lspci
``` make sure the card is listed
The card should be listed even if it doesn't work.
```
ifconfig
``` there should be at least two devices listed (lo and eth0). There may be more if you have two cards, wireless, etc. Check to see if the MAC address matches.
If there isn't an "eth0" entry, try ```
sudo ifconfig eth0 up
```

If the card is listed in "ifconfig", then it's a matter of getting it activated. 
On a DHCP network:
```
sudo dhclient eth0
``` will request a new IP address from the network. Replace "eth0" with your device name (whatever ifconfig found earlier).


Post back with the results

---

### Post by Phuzzy_one on 2008-04-07
it is seeing the NIC, when i ran sudo dhclient eth0, it stated that it did not receive any dhcp offers, i know my modem is sending out offers because it works in windows just fine,

---

