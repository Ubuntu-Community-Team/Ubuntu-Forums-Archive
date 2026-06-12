---
title: "lost my wifi!"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by dimothy10 on 2007-01-19
I have just successfully installed drivers for my ati radeon x850xt using the wiki mentioned in the forum here.  unfortunately i have now lost my wifi card.  it is listed under lspci but does not appear under iwconfig or under teh network manager.  it is a d-link dwl-g520 and i had installed the mad-wifi drivers so i could use kismet to find my ssid.  am a bit of a newb when it comes to linux but was wondering if anyone knows of any steps in the the ati wiki that might have disrupted my wifi card by accident.

cheers

tim

---

### Post by jpeddicord on 2007-01-19
Try running these steps in the terminal, in order:
```
sudo modprobe ath_pci
sudo depmod
sudo /etc/init.d/networking restart
```I have the same card, and it works fine in Dapper, but it is an absolute PAIN to get it to work right in Edgy. I had to install the madwifi-old drivers.

---

### Post by dimothy10 on 2007-01-19
tried what you recommended but to no avail.  the strange thing was that it was working before using the madwifi under designation ath0.  since i installed the ati drivers though so i could have a better resolution they card is no longer listed in iwconfig but is listed under lspic!  am stumped and am unsure about how to uninstall all the drivers i installed and start again (as i would normally have done under xp).  thanks again

---

### Post by ubuntu_demon on 2007-02-22
dimothy10 did you solve your problem ?

jacobmp92 did you try the card with WPA2 personal with CCMP/AES?

---

