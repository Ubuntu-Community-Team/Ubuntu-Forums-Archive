---
title: "xserver-xgl help"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by mason215 on 2008-02-14
Iam trying to get desktop effects working but whenever i try to install xserver-xgl and then reboot it just hangs at the light brown screen and then puts me back at the login screen here's some info

mason@mason-desktop:~$ lshw -C video
WARNING: you should run this program as super-user.
*-display
description: VGA compatible controller
product: VT8378 [S3 UniChrome] Integrated Video
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
configuration: latency=32 mingnt=2
mason@mason-desktop:~$ glxinfo | grep -i direct
direct rendering: Yes


thanks

---

### Post by spiderbatdad on 2008-02-14
have you tried installing linux-restricted-modules to see if it offers a driver for your card?

There is also a xserver-xorg-unichrome driver, but it looks like it's for older versions of the card. It may help.

---

### Post by mason215 on 2008-02-14
> **spiderbatdad said:**
> have you tried installing linux-restricted-modules to see if it offers a driver for your card?

There is also a xserver-xorg-unichrome driver, but it looks like it's for older versions of the card. It may help.

sorry, but how exactly could i do this

---

### Post by spiderbatdad on 2008-02-14
Both programs are in synaptic package manager. If you install linux-restricted-modules, i believe you need a reboot before any new drivers show up...if there are any, you should receive an alert. They would be located in Administration>>Restricted Drivers Manager.

---

### Post by mason215 on 2008-02-14
> **spiderbatdad said:**
> Both programs are in synaptic package manager. If you install linux-restricted-modules, i believe you need a reboot before any new drivers show up...if there are any, you should receive an alert. They would be located in Administration>>Restricted Drivers Manager.

ok just ran into a problem it wont let me boot ubuntu now. So can you give the commands to uninstall those 2 modules.
thanks

---

### Post by spiderbatdad on 2008-02-14
```
sudo apt-get remove --purge linux-restricted-modules
sudo apt-get remove --purge xserver-xorg-unichrome
```

The restricted modules package should not be the cause, though.

---

