---
title: "fgrlrx keeps going back to mesa"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-09-25
hey there, i installed the ATi driver 8.40 not a problem, but after awhile ive been on the computer i try fglrxinfo and it keeps going back to this :

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

then my graphics slow down a heeell of a lot, this is kinda irritating cause it reverts to mesa without me even knowing

anyone know of a solution for this?

btw using sudo dpkg-reconfigure -phigh xserver-xorg and choosing 'ati' does not help either :S

---

### Post by bobplano on 2007-09-25
when you reconfigure the xserver choosing ati means you want to use the open source drivers. just thought you would like to know. 

are you doing anything that might mess around with your xorg.conf? make sure the drivers are set to fglrx since you were choosing ati when you reconfigured X. also if you want to do dpkg-reconfigure if you scroll down some there's fglrx

---

### Post by overdrank on 2007-09-25
> **dynamethod said:**
> hey there, i installed the ATi driver 8.40 not a problem, but after awhile ive been on the computer i try fglrxinfo and it keeps going back to this :

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

then my graphics slow down a heeell of a lot, this is kinda irritating cause it reverts to mesa without me even knowing

anyone know of a solution for this?

btw using sudo dpkg-reconfigure -phigh xserver-xorg and choosing 'ati' does not help either :S

Also what Ati card are you using and have you tried to enable the restricted drivers?

---

### Post by dynamethod on 2007-09-25
yup enabled driver this is what it usually shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6747 (8.40.4)

im using a ATi X00-XT AGPx8

but after a while it go's back to the mesa thing :S

even if im not doing anything at all, like i just leave my desktop be for a couple hours, come back and the bloody thing is using mesa again!

---

### Post by asmoore82 on 2007-09-25
I had to jump through several hoops to get the ATI driver's generic installer to work
consistently on Ubuntu; but "All's well that ends well!"

But as said right above^^ you need to make sure you are choosing the ``fglrx'' driver and not ``ati'' ...

ati: generic Free and Open Source ati driver
radeon: Free and Open Source driver for Radeon cards; provides decent speed 2D graphics acceleration
fglrx: proprietary ATI driver with full speed OpenGL and TVOut support

This is what finally did the trick for me:
I had to make a symbollic link/soft link/ or "shortcut" to the /usr/lib/dri folder in /usr/lib/xorg/modules ...
```
$ sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/
```

**and Then re-install the driver with ATI's installer.**

P.S. I seem to recall that I had also blacklisted Ubuntu's stock ``fglrx'' "restricted" driver
so that it would not load instead of the updated one from ATI. I did this by following
some thing I read in a post here.

---

### Post by mintcoffee on 2007-09-25
Usually this means the fglrx-kernel package hasn't been installed properly, or something overwrote one of the files, or changed a symbolic link. This usually happens after a kernel update.

In order to fix this, just rebuild the package:

```
sudo module-assistant build fglrx
sudo module-assistant install fglrx
```

---

### Post by dynamethod on 2007-09-25
cool ill try that, thanks everyone :)

---

### Post by dynamethod on 2007-09-27
ffs, still happening, this is really really getting on my nerves now,

---

### Post by overdrank on 2007-09-27
> **dynamethod said:**
> ffs, still happening, this is really really getting on my nerves now,

Hi are you still having the same issue?

---

### Post by dynamethod on 2007-09-28
unfortunatly yes :S

---

### Post by overdrank on 2007-09-28
> **dynamethod said:**
> unfortunatly yes :S

Hi sorry it took so long to respond, Have you taken a look at this 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2)

---

### Post by dynamethod on 2007-10-02
i followed that guide, still im getting the same thing with mesa, just tried envy as well, but again, its always going back to bloody mesa

---

### Post by kellemes on 2007-10-02
Have you looked in /var/log/Xorg.0.log after a failed session?

---

### Post by dynamethod on 2007-10-02
ahh cool thanks for the tip i found this in the log:

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

but i dont quite understand it fully, am i meant to update X.org?

---

### Post by dynamethod on 2007-10-02
im really lost now because the x.org version it says it needs is the one thats installed! so what the hell?

no updates in synaptic, no nothing

---

### Post by misfitpierce on 2007-10-02
Did you use Envy to install graphics? It makes sure to auto do it all right and ends up perfect. Never a problem with envy. Configuring yourself can cause some errors if certain things are not done properly. Try envy

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb)

---

### Post by dynamethod on 2007-10-02
ya this is after i installed with envy, still getting this mesa probelm

---

### Post by dynamethod on 2007-10-02
ok just done a reinstall with envy again, all is working well now 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6747 (8.40.4)


hopefully it doesnt revert back to mesa again

---

### Post by kellemes on 2007-10-02
> **dynamethod said:**
> ahh cool thanks for the tip i found this in the log:

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

but i dont quite understand it fully, am i meant to update X.org?

Maybe it means you need a newer fglrx driver..
Anyway.. it seems they don't match for some reason..
I'd investigate the release notes of the fglrx-driver and see if your xorg- version is supported.

---

### Post by dynamethod on 2007-10-05
its happening again -.- 

i went over to dads for tea and came back and i checked fglrxinfo and it was using mesa again, while i was away for tea i had the computer on, nothing running just screen saver (when screen fades out) but when i rebooted it went back to using fglrx, so what could possibly be causing this, 

one otherthing off topic sorry but i have to ask, sometimes when i open up firefox, my homepage is set to the ubuntu forums, it asks me to download and save or open a .php file, whats with that?

---

