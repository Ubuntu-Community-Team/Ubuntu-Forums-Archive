---
title: "Nvidia driver problems"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-17
When I increase the resolution to the native resolution of my monitor, The screen goes nuts and ends up in a garbled mess on the bottom.  Is there any hope to fixing it.

---

### Post by overdrank on 2007-10-17
> **Dapman01 said:**
> When I increase the resolution to the native resolution of my monitor, The screen goes nuts and ends up in a garbled mess on the bottom.  Is there any hope to fixing it.

HI and I am glad to see you are up and running again. Could you post the output of this command```
cat /etc/X11/xorg.conf
```

---

### Post by Beggar on 2007-10-17
Is this fiesty?

Gutsy loads up fine, but if you try and make any change, add a monitor, change resolution, etc. Dynamically it does what your saying and implodes half way down the screen.

---

### Post by Azakus on 2007-10-17
The nvidia-glx-new drivers are screwed up. Manually download the nvidia driver from the site and build it like this (save as nv_newbuild.sh)
```

#!/bin/bash
echo "CLOSE AND SAVE ALL PROGRAMS BEFORE RUNNING! THIS KILLS XSERVER TO BUILD!"
echo "Type yes into the ready? prompt when ready"
echo -n "Ready?:"
read REP
If [ $REP = "yes" ]
sudo /etc/init.d/gdm stop
mkdir ~/NVIDIA
cd ~/NVIDIA
if [`uname -m` = "x86_64"]
then
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.19/NVIDIA-Linux-x86_64-100.14.19-pkg2.run
else
wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run
fi
chmod +x NVIDIA*
sudo ./NVIDIA*
```
Should work as long as I didn't leave an open if statement anywhere.

---

### Post by Hobo Joe on 2007-10-17
What method did you use to install the drivers, and what version were they?

---

### Post by AMDBuntu on 2007-10-17
If you have the latest Nvidia driver try this in terminal

gksudo nividia-settings

That should bring up the Nvidia Control panel. Giving you more frequency options...

---

