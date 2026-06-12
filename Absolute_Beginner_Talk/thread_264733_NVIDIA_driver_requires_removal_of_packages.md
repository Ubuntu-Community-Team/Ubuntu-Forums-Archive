---
title: "NVIDIA driver requires removal of packages"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Chris Johnson on 2006-09-25
I installed the NVIDIA driver nvidia-glx in order to support higher refresh rates and resolutions than the 'vesa' default driver. This worked fine for several reboots, until I got the X error that it couldn't find the driver 'nvidia'. Having switched it back to the default driver, looking in Synoptic Package Manager reveals that nvidia-glx is no longer installed, and to install it requires the removal of many packages, including things like gnome-volume-manager and vlc. Is there any way I can avoid uninstalling these things? Even if I do ask to uninstall them, I get the error:

nvidia-glx:
 Depends: libglu1-mesa but it is not going to be installed or
	libglu1

I'm not looking for fancy graphics performance - I just want a way to run my desktop at 1280x960 80Hz rather than 1024x768 60Hz, so if there's a way of getting this which doesnt require installing the Nvidia driver, I'd be happy with that.

Many thanks

---

### Post by dmizer on 2006-09-25
have you tried:
```
sudo aptitude install libglu1-mesa
```

don't know much about nvidia drivers, but usually when you have dependency problems like that, you can just install them seperately.  give it a shot and see what happens.  if nothing else, it will probably give you a better idea of what's wrong.

---

### Post by Chris Johnson on 2006-09-25
libglu1-mesa is definitely installed. Trying to install nvidia-glx through the command line gives this:

```

$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: libglu1-mesa but it is not going to be installedor
                       libglu1
E: Broken packages

```

Any further ideas on how to get this installed?


I tried switching the Driver = ... line in xorg.conf to "nv" which I believe is the free nvidia driver - but it sent my monitor into its "Out of Range" display. If it might help, is there a way to restrict the refresh rates that X tries to achieve for the resolutions listed in xorg.conf?

---

### Post by dmizer on 2006-09-25
use aptitude instead of apt-get.  it will give you more information about what the problem is, and offer solutions.

try aptitude install libglu1 instead and see if that corrects the problem.

---

### Post by Chris Johnson on 2006-09-25
Thanks very much for the help dmizer - aptitude revealed that libgl1-mesa-swrast was `broken' and found a way of resolving the dependencies.

For the benefit of other Linux newcomers who are having trouble with the Nvidia drivers, I'll mention that when I had got nvidia-glx installed, and ran nvidia-glx-config, it misdetected my graphics card model (an onboard NVidia 6100), and thus X failed to start. Replacing xorg.conf with the original one and just switching the driver from 'vesa' to 'nvidia' got X to load fine with the Nvidia drivers.

---

