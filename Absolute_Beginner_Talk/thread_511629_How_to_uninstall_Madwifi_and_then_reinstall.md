---
title: "How to uninstall Madwifi and then reinstall?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Rovdjur on 2007-07-28
Well I believe that I am using the Madwifi drivers to detect my wireless card in Kubuntu Feisty Fawn. It detects the card and AP's, but will not connect to them unless I am less than a foot from the router, so I would like to uninstall Madwifi and then reinstall it with a fresh install.

The drivers were loaded out of the box when I installed Kubuntu, so I have not done anything personally to them yet.

So what would be the best way to rid my system of the Madwifi drivers and then reinstall them?

I am fairly certain I am using Madwifi, lspci shows this as my wireless card:

```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

Help is appreciated, thanks!

---

### Post by Rovdjur on 2007-07-28
Bump :(

---

### Post by ugm6hr on 2007-07-28
I am not sure that re-installing madwifi will work...

If you want to check which driver you are using:
```
lshw -C network
```
Mine shows up as ath_pci (for Atheros 5005G)

To confirm that madwifi works:
```
lspci -nn
```
Check the PCI ID [xxxx : xxxx] at the end of the line, and compare it to the list here:
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

