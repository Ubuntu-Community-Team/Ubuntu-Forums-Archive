---
title: "Small problem with wireless on reboot"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by somethingkindawierd on 2008-04-30
I am running 8.04 on a second gen Macbook.  I followed [these instructions]("http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/") to get madwifi up and running and all worked beautifully.  Accept, on reboot, I have no wireless.  I have to run the last two commands again:
```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```
Then wireless works immediately.  Any idea on how to get this service to work on reboot?

---

### Post by cyberdork33 on 2008-04-30
add "ath_pci" to /etc/modules

---

