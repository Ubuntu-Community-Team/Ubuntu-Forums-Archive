---
title: "display drivers/xserver completely screw up"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by tamird on 2007-04-12
OK, so I started my stroll down linux lane with Feisty last week. My first attempt at doing something non-basic was getting worldofwarcraft to run with WINE.

Naturally, this involves installing the restricted NVIDIA drivers for my vid card. Being the noob that I am, I found instructions for how to do it on Edgy, and followed them.

Everything was fine until I installed some 150 updates via update manager the other day, and the next time I rebooted, my xserver crashed.

The error given was that the kernel versions didnt match...or something.

Anyway, after some experimentation, I got my GUI back, but it's not letting me run on my monitor's native 1920x1440 resolution.

My question is: how do I completely purge my system of whatever-the-crap I've got on it, and perform a correct install of the restricted NVIDIA drivers (including the appropriate xserver configuration)?

Thanks!

---

### Post by Dual Cortex on 2007-04-12
hmm, aright. When you're at the command line, type
> sudo /etc/init.d/gdm stop
then
> sudo dpkg-reconfigure -phigh xserver-xorg
and select VESA as your driver. When your done, type
> sudo /etc/init.d/gdm start

*Hopefully*, you'll see a GUI. Aright, now what you need to do (since feisty is that nice) is install the restricted drivers the *feisty* way. This involves installing the 'restricted drivers.' Now, you find the app. to install them probably by looking for its launcher under **System>Administration** (not completely sure as I don't have feisty on right now nor have I messed with it much yet). The nvidia drivers should show up there as an option. Select them and click on enable. Ubuntu should automatically start downloading the drivers, etc., and install them for you. Once done (if everything goes right and as expected) a simply ctrl+alt+del will be all that's needed to get the drivers working.
Check back once you're done (or once you're stuck somewhere) with the instructions.

---

### Post by overdrank on 2007-04-12
> **tamird said:**
> OK, so I started my stroll down linux lane with Feisty last week. My first attempt at doing something non-basic was getting worldofwarcraft to run with WINE.

Naturally, this involves installing the restricted NVIDIA drivers for my vid card. Being the noob that I am, I found instructions for how to do it on Edgy, and followed them.

Everything was fine until I installed some 150 updates via update manager the other day, and the next time I rebooted, my xserver crashed.

The error given was that the kernel versions didnt match...or something.

Anyway, after some experimentation, I got my GUI back, but it's not letting me run on my monitor's native 1920x1440 resolution.

My question is: how do I completely purge my system of whatever-the-crap I've got on it, and perform a correct install of the restricted NVIDIA drivers (including the appropriate xserver configuration)?

Thanks!

Hi I believe that when you updated your system that updated the kernel and that rendered you nvidia drivers out of luck. If you install the binary drivers then every time you update your kernel then you have to reinstall the nvidia drivers. Hope this helps Good luck!

---

### Post by tamird on 2007-04-14
Ok I followed your instructions and it seems to be configured properly. Xserver is using NVIDIA as the video device and the restricted driver menu is showing that the Nvidia driver is enabled. However, my screen res still wont go above 1024x768 (compared to the screen's native 1920x1440.

Any ideas?

---

### Post by forrestcupp on 2007-04-14
More than likely what happened is that it upgraded the linux-kernel to the latest version, but didn't upgrade the linux-restricted-modules to the same version.  So all you probably need to do is upgrade the restricted modules to the same version as the latest kernel.  The reason I say this is because the same thing happened to me.  I don't know why.  It should have upgraded them both.

But you don't need to install the nvidia-glx every time the kernel updates.  It's the linux-restricted-modules that need to be the same version.

---

