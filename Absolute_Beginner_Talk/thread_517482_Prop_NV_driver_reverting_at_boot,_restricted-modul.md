---
title: "Prop NV driver reverting at boot, restricted-modules-common already set"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by getut on 2007-08-04
I am running Feisty and already had the proprietary Nvidia drivers version 1.0-9755 up and running with no issues. Every reboot was normal. So obviously I had to have already blacklisted the non-proprietary drivers in the linux-restricted-modules-common file.

Well, I just upgraded to the 100.14.11 driver set, and they compile and install fine. They startup fine, but the do not survive a reboot. I have to recompile after every reboot. In other words it is ACTING like a default install does when you first install the proprietary driver, but don't have the non-proprietary one blacklisted. I checked again and NV is still listed in the linux-restricted-modules-common file.

It is reproducible on my machine, I have gone back to the 1.0-9755 driver and it survives reboots again. Back to the 100.14.11 and the issue returns. I did the same upgrade on my Feisty machine at work and it does fine.

The xorg.0.log file ends up with this info after the reboot (but remember it works fine after a recompile with no changes to xorg.conf).
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by getut on 2007-08-06
I still haven't found a resolution to this one. Anyone got any ideas?

---

### Post by getut on 2007-08-17
I am still fighting this. Can someone please help? At every reboot I have to recompile the kernel modules just as if I didn't have the default driver blacklisted, even though I do.

I'm sure this will be a simple fix, but I've searched for a week and still can't find the answer. Every topic about this goes back to needing to blacklist the nv driver which is already done.

I can go back one level on the nvidia driver and it retains the settings between reboots.

---

### Post by Hobo Joe on 2007-08-17
Use Envy to install the drivers. Link is in my sig.

You may have to reinstall your current ones before installing the new ones.

---

