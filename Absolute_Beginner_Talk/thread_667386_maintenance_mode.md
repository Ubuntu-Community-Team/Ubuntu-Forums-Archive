---
title: "maintenance mode"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by the bogs on 2008-01-14
i recently changed my monitor and now i cant see anything!

i know i need to get into maintenance mode or  safe graphics mode but i cant remeber the buttons to press to force this mode!!

I dont get a grub loading screen...

---

### Post by taurus on 2008-01-14
You probably don't see the GRUB menu so press the Esc when you first turn on, after the BIOS display, would bring it up.  You probably have 3 seconds to press Esc or it will just boot into default kernel.

Then, run 

```
dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure your X server.  When you're done, reboot with

```
shutdown -r now
```

---

### Post by dgray_from_dc on 2008-01-14
I've been wondering how to do that.  Thanks!!

---

