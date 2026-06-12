---
title: "Needing to reboot often..."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by rolheika on 2007-10-31
I'm slightly frustrated, as there have been instances where when the Ubuntu loading screen pops up, the orange thing only fills 3 1/4 of the rectangles and then stops moving, and nothing happens.  Do I need to reinstall Ubuntu whenever there is a problem like this, or is there another, easier, way to fix it?  I'm running a dual-boot with Vista, by the way.

---

### Post by taurus on 2007-10-31
Why don't you edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove the **quiet** near the of the line for kernel.  Then, you would know which process causes the system to hang at the boot screen.

---

### Post by Regel on 2007-10-31
Or edit it in grub (e) if it stops before you get a chance to edit menu.lst.

---

