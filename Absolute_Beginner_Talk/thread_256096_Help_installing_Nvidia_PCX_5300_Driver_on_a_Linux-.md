---
title: "Help installing Nvidia PCX 5300 Driver on a Linux-amd64-generic kernel"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-12
I need to install the nvidia driver for my card 
So far i have installed the nvidia-glx package from synaptic 
and  checked that linux-restricted-modules is installed
then i typed sudo nvidia-glx-config-enable
and it gave me an error 

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

and i changed the xorg.conf the nv to nvidia and i restarted the x server and got the nvidia flash screen 
but i dont see any changes still when minimizing then maximizing a window i see the black rectangular traces of the window like it's shadow ..is that normal for everyone ??? and how can i check that the nvidia is fully functional now other than that splash screen ??
Any help

---

