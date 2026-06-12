---
title: "1900x1600 screen resolution not available."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by HairlessMonkey on 2008-04-14
Hi,

I have a Dell Latitude D830 with an nVidia Quadro NVS 135M graphics card.
I'm running Gutsy Gibbon and have tried to install the correct drivers for the card
but the available options in the screen resolution settings does not include 1900x1600.

Searching in synaptic for nvidia tells me that the following packages are installed,
all at their latest versions.

linux-restricted-modules-2.6.22-14-generic
nvidia-glx-new
nvidia-kernel-common
restricted-manager
restricted-manager-core
smartdimmer
xserver-xorg-video-nv.


Please advice me, what steps should I try in order to fix this?

---

### Post by Tatty on 2008-04-14
ok first check that your graphics driver is correctly loaded:

```
glxgears
```

type that in a terminal, every few seconds it will give you its FPS, if it is in the 1000's then the driver is probably working.

next try ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure X


If after that you still dont get an option, try System->Administration->Screens and Graphics to set up your monitor.

---

### Post by HairlessMonkey on 2008-04-14
Thanks for the quick reply.

Those steps worked. Thanks again.

However, when trying to connect and configure a separate monitor, I lose the high resolution choices in the settings menu and the highest available is 1600x1200.
Im running dual boot with windows on the laptop and having the higher resolution works
when Im in windows so its not a hardware problem.

Does this seem familiar to anyone?

---

