---
title: "IBM Thinkcentre A50: no display after suspend"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ahorriblemess on 2008-02-25
I just installed Ubuntu 7.10 on my IBM Thinkcentre A50 8148cgu. I'm not sure if the computer is coming back after suspend. It starts up, but I get no display. Could it be that my nVidia driver isn't truly recognized? Here's my X11/conf

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

At installation, I enabled the restricted driver, I made sure my linux restricted modules were installed as well. 

If it's not the graphics card, then what could it be?

---

### Post by spiderbatdad on 2008-02-25
There are a lot of bug reports relating to thinkpad hibernate/suspend issues. Some suggest too little swap memory, and incorrect swp settings in fstab. I remember seeing other reports, too, with other work arounds. Take a look at this example.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54382](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54382)

/dev/hda5 is a swap partition with the size 1.5GB, and it is in fstab:

/dev/hda5 none swap sw 0 0

However:

wolverian@pupu:~$ LC_ALL=C sudo swapon -a
swapon: /dev/hda5: Invalid argument

---

