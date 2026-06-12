---
title: "proprietary drivers"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by skyydiiver on 2008-02-24
Hello everyone. I installed Kubuntu last night for the first time. I have used Ubuntu in the past but I could never get my printer to work and the video would only go to 600 x 800 no matter what I do. I thought I would give it another try but with KDE this time. After I installed the screen resolution was at 1280 x 1024 like it should be. This was done by default with no input from me. Since I only use my computer for the internet and watching movies ;) and never for gaming I should have just left it alone and tried to configure my printer so I can forever delete MS. Instead I started to tinker and I enabled the proprietary drivers for the video card. Everything was working fine until reboot. Now after the initial Kubuntu screen the monitor goes black. When I hit the power button the Kubuntu screen comes back with the backward slider showing that it's powering down. I can boot in safe mode to the prompt. Can anyone tell me how to revert back to the default video drivers with text inputs? Thanks

---

### Post by Crooksey on 2008-02-24
What video card do you have?

---

### Post by Iceni on 2008-02-24
Unless you share your vide card it is hard for us to know what your default driver is:)

Here's how to change driver (this shows how to change to the basic driver) :

go to a console

```
sudo nano /etc/X11/xorg.conf
```

Scroll down till you find your video card. Mine looks like this:

> Section "Device"
	Identifier	"nVidia Corporation NV41 [GeForce 6800 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection


Scroll down to your video device and change driver to "vesa" (basic driver - your should replace with your default driver).

---

### Post by skyydiiver on 2008-02-24
I have the ATI RADEON X300 SE 128MB installed.

---

### Post by skyydiiver on 2008-02-24
bump... thanks

---

### Post by Crooksey on 2008-02-24
have you tried using the ati setup?

```

$ sudo aticonfig --iniital
```

---

### Post by skyydiiver on 2008-02-24
no I haven't. I'll try it.

---

### Post by skyydiiver on 2008-02-24
OK nothing has worked so far. But..., since this is a fresh install to begin with, I'm going to reinstall the whole thing. I'll figure out how really fix it later. I would rather spend 30 minutes reloading than hours trying figure out how to fix it. Thanks to everyone who replied.

---

