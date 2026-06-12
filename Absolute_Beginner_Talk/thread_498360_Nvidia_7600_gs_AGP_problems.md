---
title: "Nvidia 7600 gs AGP problems"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Hrenojed on 2007-07-11
I am trying to install drivers to get rid of 1024*786 resolution and 50 Hz, which is killing my eyes.

First after I installed Ubuntu, set up DSL, is that I enabled Restricted Drivers Manager. It doesn't work, I still can't get higher resolution/Hz.

Then I downloaded that program for automatic installing drivers (I forgot the name, but I'm sure you know which I mean), clicked automatic Nvidia drivers install, and after the restart, I have error with gray screen that is very strange, a corners are moved.. and it tells that something is wrong and it sends me to console.

Then I formated and installed Ubuntu again. Then I did in console:
sudo apt-get install nvidia-kernel-common nvidia-glx
nvidia-glx-config enable
CTRL+ALT+Backspace

This gave me same error as up. Does anyone knows solution in console, because I really don't want to install Ubuntu all over again to get same error?

EDIT: A few last lines of xorg.0.log

> (II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found


Thank you
Hreno

---

### Post by confused57 on 2007-07-11
I don't know, but it might help to use the nvidia-glx-new driver:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by Hrenojed on 2007-07-12
This looks very confusing, is there any other way?

---

### Post by Hrenojed on 2007-07-13
Now I managed to install Nvidia drivers with Envy, and the installation went fine. But then, I couldn't put resolution higher than 1024*786 and refresh more than 75Hz. I found some tips on google how to increase resolution, but after that, the X crashed. The copying backup of xconf didn't work.

I'll have to install Ubuntu 4th time now and I really don't want to do it more. Please help.

Thank you

---

### Post by Pheodax on 2007-07-13
If you can't set your refresh rate higher it's probably not supported by your monitor. Your graphics card doesn't necessairily have to be the problem. What's the highest refresh rate you can get with a 1024x768 resolution in Windows with the same monitor?

---

### Post by AlexenderReez on 2007-07-13
i'm using 7900 gs..look at my post there...hope it can help ....

> [http://ubuntuforums.org/showthread.php?p=3015663&posted=1#post3015663](http://ubuntuforums.org/showthread.php?p=3015663&posted=1#post3015663)

---

