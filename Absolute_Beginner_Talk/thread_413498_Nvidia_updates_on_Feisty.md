---
title: "Nvidia updates on Feisty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Pizarro on 2007-04-19
I've just updated to feisty and everything seems to work ok........ But it states software updates are available for my 7600 gs nvidia card. Nvidia-glx and nvidia-glx-dev. When I press install I get the message

E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev

Not sure what this means. The upgrade was from Edgy which was running using drivers from envy program. Looking at Tux Racer and the screensavers open gl is running as before.
Nvidia x server settings states I'm using   1.0-9755

---

### Post by ruibuntu on 2007-04-19
If you really have that version installed, there are no really any updates, I guess??

:confused:

---

### Post by Tine on 2007-04-19
I had this problem also. This is how i fixed it.

Uninstall Nvidia drivers with envy

then i changed from xorg.conf "nvidia" to "nv" in the device section
restarted X server.

Then ubuntu suggested reboot, but i didn't because my upgrade wasn't succesful

then: gksudo "update-manager -c -d"

install all the packages, reboot
then i downloaded this: 
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

stopped X and installed that package and started X again

that package may need chmod a+x before you can run it

---

### Post by Pizarro on 2007-04-19
Thanks I'll try that 
:)

---

### Post by lionel47 on 2007-04-21
> **Tine said:**
> I had this problem also. This is how i fixed it.

Uninstall Nvidia drivers with envy

then i changed from xorg.conf "nvidia" to "nv" in the device section
restarted X server.

Then ubuntu suggested reboot, but i didn't because my upgrade wasn't succesful

then: gksudo "update-manager -c -d"

install all the packages, reboot
then i downloaded this: 
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

stopped X and installed that package and started X again

that package may need chmod a+x before you can run it

My card runs fine except for that message that I have an update and the resulting errors.  In your procedure I quoted, are you replacing the driver that was originally installed by envy with a different one?  My question is, why not just uninstall it with envy, change the xorg.conf, and then reinstall it again?  I'm trying to understand what your procedure is doing before I do it.  Thanks.

---

