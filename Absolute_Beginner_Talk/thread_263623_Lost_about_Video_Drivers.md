---
title: "Lost about Video Drivers"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by IgnacioMiller on 2006-09-23
I used EasyUbuntu to install Nvidia Graphics Drivers on my Ubuntu64 system a few days ago. I opened up the xorg.conf and I found this:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
```

Does this mean that my driver was not installed correctly? I also read about changing certain things in the xorg.conf in order to fully install the drivers but I could not locate a full list of what I needed to do. Any help would be greatly appreciated!

For information sake, here is my lspci -n | grep 0300 output because my Nvidia card is an integrated one, so I am not sure of the exact model:
```
0000:00:05.0 0300: 10de:0240 (rev a2)

```

Thanks,
Dan

---

### Post by Perfect Storm on 2006-09-23
change "vesa" to "nvidia"

if it fails you can 
sudo nano /etc/X11/xorg.conf
to change it back to vesa

---

### Post by IgnacioMiller on 2006-09-24
Perfect! Thank you!

Dan

---

