---
title: "API mismatch"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by tdmsrf on 2007-12-11
Hello All,

I am new to Ubuntu and have totally screwed up my computer.

I think I have a problem with my X server.

After updating the driver for my graphics card I  get an X server error and cannot proceed. 
I looked through the message and found this:

"API mismatch: The Nividia Kernel Module has the version 1.0-9755 but the X Module has the version 1.0-963"

Now what do I do?

Many thanks in advance. 

Aloha

---

### Post by nikoPSK on 2007-12-11
possibly a xorg reconfigure?
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by PriceChild on 2007-12-11
Uninstall all versions of the ubuntu driver. This includes nvidia-glx, nvidia-glx-new and nvidia-glx-new packages, as well as any custom installs you have made.

Then reconfigure the xserver to defaults and remove another possible problem:```
sudo dpkg-reconfigure xserver-xorg -pcritical
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```Next, log out, then ctrl+alt+backspace to restart the X server using the standard "nv" driver. Log in, then use system > admin > restricted driver manager to install the ubuntu nvidia drivers.

(If the old nvidia doesn't unload properly, you may need to "sudo rmmod nvidia" from the cli then try starting the xserver again... or just rebooting)

---

