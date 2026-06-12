---
title: "Geforce 8800 GTX makes my monitor display an error"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by gamer4lyf3 on 2008-03-03
I have a geforece 8800 GTX video card. and a rosewill r912E display
I'm trying to use the geforece 8800 GTX drivers instead of vesa because I want to have the cooler effects enabled (system -> preferences -> appearances -> Visual effects). When I attempt to enable "extra" visual effects it tell me I have to use "NVIDIA accelerated graphics driver (latest cards)" If I say ok I get back to the desktop after a restart and an annoying box is bouncing around my display saying "Input is not supported". I have no idea how to get this box to go away other than going back to Vesa display drivers.
Can anyone help me please?

---

### Post by hhhhhx on 2008-03-03
install the nvidia drivers, easiest way is probably through envy :)

---

### Post by gamer4lyf3 on 2008-03-03
THanks for a replay!
Umm but one problem hah,
How do I go about istalling envy? :)

---

### Post by hhhhhx on 2008-03-03
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

nice graphics card BTW

---

### Post by uberlube on 2008-03-03
Or you can grab it from the repositories using the Synaptic Package Manager

---

### Post by gamer4lyf3 on 2008-03-04
Thanks, I don't even play games anymore so I don't even know why still have it hah.
but I tried to run 'sudo nvidia-glx-config enable' and it gave me the following error

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

If I edit my xorg manually do I just have to change the one play I see "nv" to "nvidia" and thats it?

---

### Post by hhhhhx on 2008-03-04
looks like it :)

---

### Post by gamer4lyf3 on 2008-03-04
:-( didn't work heres what I did.

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	0
EndSection

I changed the "nv" to "nvidia" in the 5th line of the xorg and when I rebooted it said that It couldn't detect my video input or something and to configure my settings for my video card (same as system -> administrator -> screen and graphics ->) I changed it from vesa to nivdia and rebooted. But it gave me the same error so I just went back to "nv" and I have that annoying box bouncing still :-(.

---

### Post by gamer4lyf3 on 2008-03-04
Alright well yesterday it all went up in smoke so I decided I would go with Envy. I've got in installed and it has even installed the Nvidia drivers on my computer but now I don't know how or what driver to enable for the geforece 8800 GTX video card I'm still on vesa. Is there a way that I can get Envy to auto detect the driver I need to enable and have it do so for me?

---

