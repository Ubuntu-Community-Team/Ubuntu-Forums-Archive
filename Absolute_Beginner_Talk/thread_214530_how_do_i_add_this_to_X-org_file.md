---
title: "how do i add this to X-org file?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-12
I am using Kubunru desktop and i want to enable transparency and i was told this everytime i start the system to do this. but i dont know how, i was told this:

> Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

how exactly do i this please?

---

### Post by reacocard on 2006-07-12
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf

```
that will back up your xorg.conf (in case you screw up), and then open a text editor for xorg.conf. just add those lines to the end, save, and reboot.

---

### Post by maddbaron on 2006-07-12
thank you very much

---

