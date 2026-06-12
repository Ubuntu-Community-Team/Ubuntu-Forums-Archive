---
title: "Video problems after using envy"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by zakunin on 2007-05-03
I've tried in different way to install my GeForce4 MX 440 AGP 8x drivers and, using envy (it was the third attempt) the GUI didn't start. I have recovered the problem reconfiguring the xserver and now i have a bad resolution of the screen and i cannot do some operations like to adjust colors with the video player...
So...
what i have to do to reconfigure in the right way xorrg.conf? when i have reconfigured the xserver, the nvidia drivers where are finished? There are particular drivers for my GeForce?

thanx!

---

### Post by matburton on 2007-05-03
Not sure if I completely understood that but you want to revert to the default drivers?

If so then in xorg.conf change "nvidia" to "nv"

e.g.
```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
	Option		"NoLogo"
EndSection

```

Hope that helps!

---

