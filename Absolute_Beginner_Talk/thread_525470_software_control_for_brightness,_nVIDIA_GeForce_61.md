---
title: "software control for brightness, nVIDIA GeForce 6150"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Dan_472 on 2007-08-14
Hello

I would like to have a software control for changing the brightness of my monitor.  My graphics card: nVIDIA GeForce 6150 (built into motherboard).

Using Synaptic Package Manager,  I see two possibilities:  gddccontrol  and  nvidia-settings.    Both are "Not Authenticated",  and the nvidia one says it will remove nvidia-glx (did I need that to make the card work?)

Are they safe,  and which one should I use,  or neither?

Thank you very much.

---

### Post by Hospadar on 2007-08-14
If you have installed (and are using) nvidia-glx then you already have nvidia-settings installed (don't get it from the repos).  If you arn't sure whether or not you are using it, do a "gedit /etc/X11/xorg.conf" and in the "Device" secion it should the Driver line should say "nvidia".  if it says "nv" you are still using the default drivers.

If you are using the nvidia drivers, go to Applications->System Tools->Nvidia Settings and go to color correction and you can change the brightness from there.

If you arn't using the nvidia drivers, you need to enable them with the command "sudo nvidia-glx-config enable" then restart your machine and do as above.

If you are talking about backlight brightness on a laptop (I think maybe lcd monitors connected with digital cables as well) you can try the brightness applet.  right-click one of your panels, and go to "add to panel" and select the brightness applet.

---

### Post by risk on 2007-08-14
May as well hijack this thread.. :razz:

I'm trying to install the nvidia-glx package but its giving an error "dependency is not satisfiable: nvidia kernal  100.14.11"

Its quite an old card. NV11 [GeForce2 MX/MX 400]... I have my monitor brightness at 100% but its still dull. Does anyone know of another package which will support my relic of a gfx card :D?

---

### Post by Dan_472 on 2007-08-14
I think I'm using the nvidia drivers,  here's that section of xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"

Also,  I get the big "nVidia" screen when I boot-up.

But... if I click   Applications->System Tools  I can't see   Nvidia Settings

---

### Post by Hospadar on 2007-08-14
hmmm
try doing
```
nvidia-settings
``` from the command line (you are definately using the nvidia driver)
If that doesn't work try
```
sudo apt-get install sysinfo
sysinfo

```then go to the nvidia section and click the "nvidia settings"

See if either of those works

Risk:
you may need the nvidia-glx-legacy for your card.  you should use envy to install your drivers, it will pick the right ones. do a ctrl-alt-F1 to get a text terminal, and then do this
```
sudo apt-get install envy
sudo envy -t

```

Remove and clean nvidia drivers with the dialog, then install the nvidia drivers with the dialog, let it edit your xorg.conf file, and let it restart the xserver.

---

### Post by Dan_472 on 2007-08-14
doing

```
nvidia-settings
```

works great

thank you

---

