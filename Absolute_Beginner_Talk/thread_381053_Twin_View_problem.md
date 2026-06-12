---
title: "Twin View problem"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by koasati on 2007-03-10
Please someone tell me what I'm doing wrong......

I have setup the xorg.conf like this;

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	VideoRam	131072
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "CRT"
EndSection

but still have nothing but garbage on the second monitor. (after reboot)
Both monitors are indentical,  DELL D1028L

I have been reading all I could find on the subject, but I'm just getting more confused.
Do I need to edit the "Monitor" section also?
Have I done something wrong in the "Device" section?

Help this old dog learn a new trick.......... please.

---

### Post by Crooksey on 2007-03-10
change the driver from "nv" to "nvidia" assuming you have installed the nvidia-glx packages...

```

sudo apt-get update
sudo apt-get install nvidia-glx

```

---

### Post by koasati on 2007-03-10
Thanks! That did it....... I'm embrassed that I missed something so simple.

---

