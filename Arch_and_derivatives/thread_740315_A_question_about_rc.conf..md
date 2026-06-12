---
title: "A question about rc.conf."
date: 2008-03-30
forum: Arch and derivatives
---

### Post by Barrucadu on 2008-03-30
Right now, rc.conf contains a few daemons that start up. These, however, are useless without a GUI, and just take up extra memory when I'm not running one. Is it possible for me to pass a parameter through GRUB to get Arch to use a different rc.conf file? Something like "rc.conf.nodaemons"?

The reason I want to do this instead of just removing the daemons is because I would ideally like to have several entries in GRUB: "Arch Full", "Arch Server", "Arch Basic", etc.

---

### Post by Barrucadu on 2008-03-30
I got it working by following the directions here: [http://wiki.archlinux.org/index.php/Adding_Runlevels](http://wiki.archlinux.org/index.php/Adding_Runlevels)
By disabling all the daemons except the system monitor, I got the RAM usage down to 26MB!

---

