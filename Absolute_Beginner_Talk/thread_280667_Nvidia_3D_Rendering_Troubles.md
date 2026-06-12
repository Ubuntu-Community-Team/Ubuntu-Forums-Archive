---
title: "Nvidia 3D Rendering Troubles"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Amackera on 2006-10-19
Sorry if this is a total beginner question, I'm absolutely as green as grass when it comes to linux. 

I'm trying to get 3D rendering enabled on my laptop. I have an NVidia card (GeForce 7800GTX). I install the nvidia driver in Synaptic, and I'm following the instructions from [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html").

When I type this into my console:

```
sudo nvidia-glx-config enable 
```

I get this message:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
anson@anson-laptop:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0099 (rev a1)

```

And if I run the command it tells me to, when I restart Ubuntu, the x server receives a critical failure (it doesn't recognize any drivers installed, I think).

Anybody have any suggestions for me?

---

### Post by CatKiller on 2006-10-19
The nvidia-glx-config enable command seems to be crap. It appears to just go through the xorg.conf and change the driver line of the first device it comes to to nvidia, regardless of what it was before, or what it should be.

Have you managed to restore the backup to get X running again? If so, you can use the command ```
gksudo gedit /etc/X11/xorg.conf
``` to edit the file manually. You can post the contents here if you'd like some help, but changing the driver of the appropriate line to "nvidia" is your ultimate goal. It's finding the appropriate line that the script doesn't seem to be able to do :)

---

