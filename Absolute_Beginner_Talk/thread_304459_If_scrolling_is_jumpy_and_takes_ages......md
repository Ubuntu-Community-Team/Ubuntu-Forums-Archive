---
title: "If scrolling is jumpy and takes ages....."
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by flameproof on 2006-11-21
If scrolling is jumpy and takes ages - a little hint from beginners to beginners...

A little trick that improved my NVidia Geforce 6100 video performance A LOT:

In terminal type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
(that backsup xorg.conf , to be safe)

Then type:

```
gksudo gedit /etc/X11/xorg.conf
```

That will let you edit the otherwise protected xorg.conf .
xorg.conf has all sort of configeration things, just like system.ini in Windows. Look for:

```
"Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

```

And change "vesa" to "nvidia"

```
"Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"	
	BusID		"PCI:0:5:0"
EndSection

```

at least pages now scroll very fast.

Any more hints I can do from here on?

---

### Post by Dual Cortex on 2006-11-21
lol...well just make sure your nvidia driver has been installed. You were just using a generic driver.
Here's the link on installing the Nvidia driver... not XTREME-NEWBIE friendly though:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by flameproof on 2006-11-21
I don't understand the "lol". What's so funny about it? That one word change gives a major improvement.

I will try the driver link later.....

---

### Post by flameproof on 2006-11-22
I tried that link:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

First part is what I did anyway. It worked up to:

xine -V xxmc filename.ts
mplayer -vo xvmc -vc ffmpeg12mc filename.ts

There I got a "xine unknown command" error from terminal.

But sounds a bit like that trick is only relevant for gamers....

---

