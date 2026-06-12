---
title: "Lost Removable Drives and Media"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by arden on 2006-04-15
Trying to get my USB Cruzer to mount I somehow managed to lose Removable Drives and Media from System Preferences. I'm trying to find a way to get it back since it was completly removed. I'm running Breezy, am I going to have to do a reinstall? Any help will be appreciated.

---

### Post by aysiu on 2006-04-15
I'm not sure if this'll help, but maybe...

Applications > Accessories > Terminal ```
sudo apt-get update
sudo apt-get install --reinstall gnome-volume-manager
```

---

### Post by mostwanted on 2006-04-15
I think the application disks-admin has similar features. It can be found in System &#8594; Administration or by issuing the command ```
disks-admin
```

---

### Post by arden on 2006-04-15
Thanks aysiu, that fixed it. I was starting to panic, did'nt realize it would be that easy to fix.

---

