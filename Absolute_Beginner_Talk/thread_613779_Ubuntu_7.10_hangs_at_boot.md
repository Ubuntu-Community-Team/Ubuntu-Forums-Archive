---
title: "Ubuntu 7.10 hangs at boot"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by netmarker on 2007-11-15
After a failed Netgear driver installation Ubuntu 7.10 hangs at boot after the following lines:

init: Error parsing configuration: No such file or directory
[46.437307] Kernel panic - not syncing.Attempted to kill init!

After these two lines the booting stops, and all I get is the prompt.

Can anyone tell me what is the problem and what can I do to fix it?

---

### Post by dajhorn on 2007-11-15
This error means that the /boot/grub/menu.lst or the /boot/initrd.img-2.6.22-14-generic file is damaged.

You should push ESC at boot time, choose another kernel, and try to install the driver again.

If the only kernel on this computer is broken, then you must use the Ubuntu installer disc (aka the Live CD)  to repair the system by reinstalling the kernel.

---

