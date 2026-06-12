---
title: "Asus N55SL-DS71 Resolution problems"
date: 2012-05-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by monk0nuggets on 2012-05-29
I've been running 12.04 for months, and today I was updating my codecs for video editing, and after rebooting the machine, it no longer seems to recognize the onboard Intel graphics. It now won't display past 640x480, which is completely ridiculous. It's got an Nvidia 635m built in also, but I haven't been using that in Ubuntu because there isn't support for it yet. So, how do I reset to the default built in video drivers? It's been working fine up until now. Help!

---

### Post by monk0nuggets on 2012-05-29
Rather than wait, I decided to just reinstall 12.04, since everything important is on another drive.  Now, the new install won't let me use Unity 3D, just 2D.

When I do this: glxinfo | grep OpenGL

I get this:

```
$ glxinfo | grep OpenGL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by monk0nuggets on 2012-05-29
And this:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev a1)
```

---

### Post by SedukiDude on 2012-11-06
I just received my ASUS N55SL-DS71 last week. I waited quite a while to upgrade to 64bit and had my eye on this DS71 because of the BluRay burner. I had been checking posts to see what kind of problems are out there with installing Ubuntu on this machine. I already have a problem with the trackpad using Windows 7 and I want to get that nailed down before wiping out Windows with Ubuntu 12.10. I plan on running Windows 7 in VirtualBox so I can countinue to run iTunes to update my Apple devices. I've been using Ubuntu for 5 years now and I am spoiled and don't want to use Windows unless it is absolutely necessary. Any help will be very much appreciated.

---

