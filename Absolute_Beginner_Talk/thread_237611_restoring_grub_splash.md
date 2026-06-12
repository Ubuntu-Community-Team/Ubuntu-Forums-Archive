---
title: "restoring grub splash"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-08-16
hi,

recently installed kde-desktop.  big mistake.  wiped out ndiswrapper and removed "shut down" and "restart" from gnome's logout window.

so i uninstalled kde, but the grub splash still reads "kubuntu" instead of "ubuntu".  when shutting down, it reads "ubuntu".  how can i change the boot splash back?
thanks,

-steve

---

### Post by Metacarpal on 2006-08-16
Here's how to fix:

In Synaptic, search for "usplash".  Find "kubuntu-artwork-usplash" and mark it for complete removal.  Find "usplash" and mark it for re-installation (or just installation if not currently installed).

If you prefer command-line:
```
sudo aptitude remove kubuntu-artwork-usplash
sudo aptitude install usplash
```

Depending on how you uninstalled KDE, you may also find [this howto]("http://www.psychocats.net/ubuntu/puregnome.php") helpful in getting all of the KDE components back off of your system.

---

