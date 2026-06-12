---
title: "Wine suddenly don't work anymore"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-19
Hi, for some reason wine simply doesn't work for me anymore, It workes yesterday, and then today it wouldn't work anymore. I use it with flashget and IE4Linux. Both programs used to run fine using wine, but now they just dont start. When I click the launcher, nothing happens.

I saw some one in another thread posting the output of: winecfg
I have no idea why, but if it helps, I have attached mine

Hope someone can help me, I have tried to reinstall, uninstall and install with automatix, reboot, install reboot again, and uninstall, reboot, and then installing and rebooting again without any luck

---

### Post by bodhi.zazen on 2007-06-19
Well winecfg is working, so wine is working as well.

Did you upgrade wine ? That is likely the culprit. Try downgrading wine (remove the current version, DL the last from wine HQ, and put the package on hold).

Download : [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Put on hold : [http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold](http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold)

---

### Post by cogadh on 2007-06-19
That winecfg had a bunch of errors related to the NVIDIA video driver. Did you recently make any changes like installing the accellerated driver instead of the generic "nv" driver?

---

### Post by arnieboy on 2007-06-19
> **kasperbs said:**
> Hi, for some reason wine simply doesn't work for me anymore, It workes yesterday, and then today it wouldn't work anymore. I use it with flashget and IE4Linux. Both programs used to run fine using wine, but now they just dont start. When I click the launcher, nothing happens.

I saw some one in another thread posting the output of: winecfg
I have no idea why, but if it helps, I have attached mine

Hope someone can help me, I have tried to reinstall, uninstall and install with automatix, reboot, install reboot again, and uninstall, reboot, and then installing and rebooting again without any luck

do this:
```
rm -rf ~/.wine

``````
winecfg
```

---

### Post by bodhi.zazen on 2007-06-19
If you do that you will loose your wine fake_c drive.

better to rename .wine to .wine.bak and then re-try winecfg

But, as you can see it is difficult to determine the problem ...

---

### Post by kasperbs on 2007-06-20
> That winecfg had a bunch of errors related to the NVIDIA video driver. Did you recently make any changes like installing the accellerated driver instead of the generic "nv" driver?
Yes I have done everything possible to my nvidia drivers, had all the available drivers installed and uninstalled a thousand times...

I tried to rename .wine and do the winecfg but nothing changed. Im now going to try and downgrade it, all though I'm sure it has been working with the new release. But its worth a try

EDIT: Tried Downgrading with no luck, still nothing happens when I try to run anything in wine

---

### Post by kasperbs on 2007-06-20
Can someone please comment on what I have done?
Ok since nothing worked for me I tried to completely uninstall my nvidia drivers, and that seemed to work as far as letting me run wine. But I'm now getting error messages from my winecfg. here is what I did:

> sudo apt-get remove --purge nvidia-glx-legacy
and then
> sudo apt-get remove --purge nvidia-kernel-common
then
> sudo apt-get install wine
then ;)
> winecfg
which gave me this plus the dialog box to configure wine
> wine: creating configuration directory '/home/rudolf/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
wine: '/home/rudolf/.wine' created successfully.
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
I just need to know if I have done something that i shouldn't have done or if it's safe for me, to keep on using my Ubuntu now as it is?

Thanks

---

### Post by cogadh on 2007-06-20
Its trying to tell you you need to install that 3D accelerated driver in order to use the OpenGL functions in Wine.  Follow the instructions [here]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") to install the driver properly.

---

