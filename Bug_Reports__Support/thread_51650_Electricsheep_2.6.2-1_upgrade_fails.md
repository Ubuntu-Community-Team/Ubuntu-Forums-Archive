---
title: "Electricsheep 2.6.2-1 upgrade fails"
date: 2005-07-24
forum: Bug Reports / Support
---

### Post by charlieg on 2005-07-24
When trying to upgrade from the default 2.5-2 version of electricsheep to 2.6.2-1, it fails with the following error message:
```
E: /var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb:
  trying to overwrite `/usr/share/xscreensaver/config/electricsheep.xml',
  which is also in package xscreensaver
```
Obviously a conflict with xscreensaver.  But how do I sort it out?  That damned red upgrade circle in the system tray is annoying me.

---

### Post by brian g on 2005-08-08
[QUOTE=charlieg]When trying to upgrade from the default 2.5-2 version of electricsheep to 2.6.2-1, it fails with the following error message:
```
E: /var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb:
  trying to overwrite `/usr/share/xscreensaver/config/electricsheep.xml',
  which is also in package xscreensaver
```
Obviously a conflict with xscreensaver.  But how do I sort it out?  That damned red upgrade circle in the system tray is annoying me.[/QUOTE]
i am having this same problem..
i tried forcing the version but that didn't help.

---

### Post by bassliu on 2005-11-09
[PHP]dpkg -i --force-overwrite /var/cache/apt/archives/electricsheep_2.6.2-1~hoary1_i386.deb[/PHP]


or maybe

[PHP]apt-get install --force-yes[/PHP]


will do fine

---

