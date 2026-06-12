---
title: "FPS and 3d support in Ubuntu"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by smokeysaysno on 2006-07-13
So I installed Ubuntu the beginning of this week.  I used easyubuntu to install mp3 and other codecs.  I also, at the time, thought it would be good to use it to update the ATI drivers for my graphics card (a Radeon 128mb 9200SE.  This turned out to be a big mistake and I had an crappy time trying to enable 3d, firstly with the 3d Mesa graphics enabled and secondly with a tonne of errors popping up when i used ```
fglrxinfo
```.

So, I reinstalled ubuntu today.  I ran easyubuntu and decided not to opt for the ATI drivers.  I randomly tried glxgears and the gears actually rotate!  Does this mean that my 3d graphics are accelerated by the standard installed ubuntu drivers?  How can i check FPS and accelerated 3d?  Any help would be appreciated.  ATI cards and linux compatibility are driving me crazy!

smokey

---

### Post by compbrain on 2006-07-15
> **smokeysaysno said:**
> So I installed Ubuntu the beginning of this week.  I used easyubuntu to install mp3 and other codecs.  I also, at the time, thought it would be good to use it to update the ATI drivers for my graphics card (a Radeon 128mb 9200SE.  This turned out to be a big mistake and I had an crappy time trying to enable 3d, firstly with the 3d Mesa graphics enabled and secondly with a tonne of errors popping up when i used ```
fglrxinfo
```.
So, I reinstalled ubuntu today.  I ran easyubuntu and decided not to opt for the ATI drivers.  I randomly tried glxgears and the gears actually rotate!  Does this mean that my 3d graphics are accelerated by the standard installed ubuntu drivers?  How can i check FPS and accelerated 3d?  Any help would be appreciated.  ATI cards and linux compatibility are driving me crazy!

smokey


Hi,

You can try running `glxinfo` in a console, that should give you all sorts of fun information about your 3d setup.

---

### Post by Anduu on 2006-07-15
The generic ATI driver that gets installed by default has very rudimentary 3D support at best.

I myself have had nothing but problems with ATI's proprietary drivers...they installed fine from what I could tell but delivered sub-par performance.

However the fglrx driver from the repos performs admirably and are quite simple to install.

Boot into recovery mode so there are no video drivers in memory

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo shutdown -r now
```

If it so happens it says they are already installed you should remove them first using apt-get remove.

After login type fglrxinfo in a terminal.You should get something like this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

---

