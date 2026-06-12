---
title: "Grub question"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jrd on 2007-02-20
What command do I pass with grub to make the system boot with low resolution? My problem is the res is too high for my monitor and so it just goes black after boot. 800x600 would be good.
Thanks in advance.

---

### Post by tgalati4 on 2007-02-20
There are several ways to do it.

Log into a "rescue shell" from a Live Disc or from grub

The grub entry to edit is:  **sudo nano /boot/grub/menu.lst**

kernel  /boot/vmlinuz-2.6.whatever-386 root=/dev/hdwhatever ro single

The "single" puts the session into single user mode.

Edit your xserver configuration file:  **sudo nano /etc/X11/xorg.conf**

remove the offending resolutions

Reboot

Be sure to back up your configuration files first:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.bak**

and

**sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.bak**

Enjoy Ubuntu goodness

---

