---
title: "MBP 3.1, ubuntu 8.10: turn off wifi and bluetooth"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by ska80 on 2009-02-17
Hi,

Is that possible to turn off wifi and bluetooth when running MBP on battery? I couldn't find any switches in GNOME's NetworkManager. 'iwconfig wlan0 txpower off' doesn't work either.

Thanks for help.

---

### Post by cyberdork33 on 2009-02-17
```
 sudo /etc/init.d/bluetooth stop
``` should kill bluetooth

To really do this though, you need to unload the modules for bluetooth and wifi.

---

### Post by deltaiscain on 2009-03-02
How would you start it again afterwards? substitute start for stop? Thanks!

---

### Post by cyberdork33 on 2009-03-02
> **deltaiscain said:**
> How would you start it again afterwards? substitute start for stop? Thanks!
yes

---

