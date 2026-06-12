---
title: "Blender on 7.04"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by nickej on 2007-04-21
I'm an utter novice with Ubuntu, testing it out as an environment for using Blender 3D. It's not happy. I did a basic install of Ubuntu Eft from a disk, and upgraded to Feisty online. I used Add/Remove programs to install Blender 243 (latest) and the install went easily. Blender launches fine.

HOWEVER--When I begin to use Blender, it locks up the system so hard and fast that I have to not only force-quit but temporarily turn off the power supply in order to allow it to reboot.
I have an ATI Radeon 8500 (according to the Ubuntu hardware report) and I see that there are some issues regarding ATI cards, so I'm assuming this may be one. What I'd like to know about is how to troubleshoot it when simply to use it freezes things up so bad.

Any advice much appreciated.

---

### Post by IgnacioMiller on 2007-04-21
Hi nickej,

Are you using a video driver that supports 3D Acceleration, i.e. the official ATI driver? I know there are some issues with that driver but I don't know what other options you have for 3D acceleration.

Hope you get your problem resolved!

---

### Post by nickej on 2007-04-21
> **IgnacioMiller said:**
> Hi nickej,

Are you using a video driver that supports 3D Acceleration, i.e. the official ATI driver? I know there are some issues with that driver but I don't know what other options you have for 3D acceleration.

Hope you get your problem resolved!

Actually, I have no idea what driver is being used. I'm new to this.

---

### Post by nickej on 2007-04-21
> **IgnacioMiller said:**
> Hi nickej,

Are you using a video driver that supports 3D Acceleration, i.e. the official ATI driver? I know there are some issues with that driver but I don't know what other options you have for 3D acceleration.

Hope you get your problem resolved!

Actually, I have no idea what driver is being used. I'm new to this. I tried installing the ATI driver available through repos but it doesn't do a thing for the problem.

---

### Post by jem7v on 2007-04-21
You'll probably want to use the right driver, then, and fortunately for you, the Radeon 8500 is actually supported by their proprietary fglrx driver.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) explains how to install it, I believe... it's for Edgy, but it'll most likely work in Feisty too.

---

### Post by nickej on 2007-04-21
> **jem7v said:**
> You'll probably want to use the right driver, then, and fortunately for you, the Radeon 8500 is actually supported by their proprietary fglrx driver.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) explains how to install it, I believe... it's for Edgy, but it'll most likely work in Feisty too.

Ah, good! Explanations!


In poking around, it also seems that Blender requires glibc 2.3.2, and Feisty automatically installs with 2.5. The last Ubuntu release that used 23.2 was Hoary....seems I'm going to have to read upon how to regress.....
Thanks for the tip on the driver!:)

---

### Post by jem7v on 2007-04-21
Pfft.  They probably mean 2.3.2 or HIGHER, because Blender worked fine in Edgy.  You shouldn't have to downgrade.

---

### Post by Patrick K on 2007-04-21
In the system administration menu there is Restricted Drivers Manager. Open it, click on enable and it will install the proper driver for you. Very easy!

---

