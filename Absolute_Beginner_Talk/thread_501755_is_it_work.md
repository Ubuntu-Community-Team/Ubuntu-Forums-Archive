---
title: "is it work?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by 3enith on 2007-07-15
i want to buy a new HDD for installing ubuntu on it .if i unplug my current HDD and install the new one and setup ubuntu on it the plug my old HDD with windows xp installed can it dualboot with windows?

---

### Post by oilchangeguy on 2007-07-15
> **3enith said:**
> i want to buy a new HDD for installing ubuntu on it .if i unplug my current HDD and install the new one and setup ubuntu on it the plug my old HDD with windows xp installed can it dualboot with windows?

if you set the drive with ubuntu as master, and the windows drive as slave, you should have no problems. install ubuntu with the drive set as master, don't change it after you install it. windows seems not to care if it's on master, or slave.

---

### Post by davec64 on 2007-07-15
No need!
Install your second drive as a slave to your main drive, then install Unbuntu on that drive. Doing it this way, when grub is installed it will pick up XP and add it to your boot menu. You could do it your way, but you'd have to reinstall Grub so it could pick up XP and add it to your boot menu.

---

### Post by xpod on 2007-07-15
If you have an option for switching between the separate drives at boot up it should`nt be a problem although just leaving your Windows drive in and installing Ubuntu to the second drive should`nt cause you any problems.

The grub bootloader would install and detect XP automatically for you giving you the option at bootup.
We have two drives on each of the desktops in the house and every single installation i`ve ever done has picked up whatever other operating systems were there at the time,including XP & Vista

---

