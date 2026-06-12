---
title: "Monitor calibration, profiles etc..."
date: 2007-12-10
forum: Art &amp; Design
---

### Post by robgr85 on 2007-12-10
Hi!

I have calibrated my screen using some calibrating device (colorvision spyder2express) under windows os, it gave me profile saved in ".icm" format.

How to force ubuntu to use this profile?

Cheers,
Robert

---

### Post by smartboyathome on 2007-12-10
I don't think you can force ubuntu to use this. You might have to callibrate it using Ubuntu native stuff. :(

---

### Post by Dragonbite on 2007-12-10
> **smartboyathome said:**
> I don't think you can force ubuntu to use this. You might have to callibrate it using Ubuntu native stuff. :(
What does Ubuntu have to do that?

---

### Post by smartboyathome on 2007-12-10
I don't know, I am just thinking out loud. Sorry. ;)

---

### Post by jcornuz on 2007-12-11
Basically, just copy your ICM file somewhere accessible and load it with xcalib. Details here: 
[http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/](http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/)

Use then a color aware application and use the same profile. Here is an example with Cinepaint:
[http://jcornuz.wordpress.com/2007/09/27/color-managed-monitor-ii/](http://jcornuz.wordpress.com/2007/09/27/color-managed-monitor-ii/)

If you feel brave (like using the command line) Spyder2 is supported in Linux and can produce ICC monitor profiles directly in Linux.
See here: [http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/](http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/)
and here:[http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/](http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/)

Take care,

Joel

---

### Post by robgr85 on 2007-12-11
> **jcornuz said:**
> Basically, just copy your ICM file somewhere accessible and load it with xcalib. Details here: 
[http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/](http://jcornuz.wordpress.com/2007/09/26/color-managed-monitor-i/)

Use then a color aware application and use the same profile. Here is an example with Cinepaint:
[http://jcornuz.wordpress.com/2007/09/27/color-managed-monitor-ii/](http://jcornuz.wordpress.com/2007/09/27/color-managed-monitor-ii/)

If you feel brave (like using the command line) Spyder2 is supported in Linux and can produce ICC monitor profiles directly in Linux.
See here: [http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/](http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/)
and here:[http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/](http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/)

Take care,

Joel

Thanks for that reply. However got some problems while installing xcalib, here these are, maybe someone can help me:

```
root@rob-laptop:/home/rob/Desktop/xcalib-0.8# make
cc -O2 -c xcalib.c -I/usr/X11R6/include -DXCALIB_VERSION=\"0.8\"
xcalib.c:52:22: error: X11/Xos.h: No such file or directory
xcalib.c:53:23: error: X11/Xlib.h: No such file or directory
xcalib.c:54:24: error: X11/Xutil.h: No such file or directory
xcalib.c:55:39: error: X11/extensions/xf86vmode.h: No such file or directory
xcalib.c: In function ‘main’:
xcalib.c:534: error: ‘XF86VidModeGamma’ undeclared (first use in this function)
xcalib.c:534: error: (Each undeclared identifier is reported only once
xcalib.c:534: error: for each function it appears in.)
xcalib.c:534: error: expected ‘;’ before ‘gamma’
xcalib.c:535: error: ‘Display’ undeclared (first use in this function)
xcalib.c:535: error: ‘dpy’ undeclared (first use in this function)
xcalib.c:842: error: request for member ‘red’ in something not a structure or union
xcalib.c:843: error: request for member ‘green’ in something not a structure or union
xcalib.c:844: error: request for member ‘blue’ in something not a structure or union
make: *** [xcalib] Error 1
root@rob-laptop:/home/rob/Desktop/xcalib-0.8#    
```  


What to do now?

Cheers,
Robert

---

### Post by jcornuz on 2007-12-12
Hi there,

you need to install the xorg development packages in order to compile xcalib.

Which architecture do you have? if i386, there is a pre-compiled library here: [http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/xcalib](http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/xcalib)

If you are on 64bits, I can send you my version.

It is a rather simple program so it should work without problem.

Take care...

Joel

---

### Post by johannes on 2007-12-13
jcornuz:
Thanks very much for the tip about xcalib. This was exactly what i was looking for.

The articles/guides you linked to were very informative. Did you write them? In that case, thanks for your work! :)

---

### Post by Paul14 on 2008-01-23
Hi,

First, thanks for your site. Very clear and usefull.

Second, I&#8217;ve downloaded xcalib (pre-compiled). So I have this file: xcalib. Where did I put it in order to Ubuntu recognized it and that I can do: xcalib /path/to/iccprofile.icc

Thank,

Valery

---

### Post by jcornuz on 2008-01-23
The answer to Valery's question is in the comments on the blog:

[INDENT]Just change xcalib’s permissions (in nautilus, right-click the file & choose allow execution like a program) and then copy it (as root) in /usr/bin with “sudo cp ./xcalib /usr/bin” assuming you are in the directory where your xcalib is.
[/INDENT]
In case it can be of help to someone else.

Take care

Joel

---

### Post by Paul14 on 2008-01-23
Thanks (again) Joel! Very quick answer and very efficient.

---

### Post by pdirty on 2008-02-09
When trying to make xcalib I get the following error:

pdirty@recycled:/usr/local/xcalib-0.8$ make xcalib
cc -O2 -c xcalib.c -I/usr/X11R6/include -DXCALIB_VERSION=\"0.8\"
xcalib.c:41:19: error: ctype.h: No such file or directory
xcalib.c:42:19: error: errno.h: No such file or directory
xcalib.c:43:19: error: stdio.h: No such file or directory
xcalib.c:44:20: error: stdlib.h: No such file or directory
xcalib.c:46:19: error: fcntl.h: No such file or directory
xcalib.c:47:20: error: string.h: No such file or directory
xcalib.c:48:23: error: sys/types.h: No such file or directory
In file included from xcalib.c:52:
/usr/include/X11/Xos.h:168:20: error: unistd.h: No such file or directory
/usr/include/X11/Xos.h:239:22: error: sys/time.h: No such file or directory
/usr/include/X11/Xos.h:240:18: error: time.h: No such file or directory
In file included from /usr/include/X11/Xos.h:294,
                 from xcalib.c:52:
/usr/include/X11/Xarch.h:62:20: error: endian.h: No such file or directory
xcalib.c:64:18: error: math.h: No such file or directory
xcalib.c: In function ‘usage’:
xcalib.c:114: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c:114: error: ‘stdout’ undeclared (first use in this function)
xcalib.c:114: error: (Each undeclared identifier is reported only once
xcalib.c:114: error: for each function it appears in.)
xcalib.c:161: warning: incompatible implicit declaration of built-in function ‘exit’
xcalib.c: At top level:
xcalib.c:226: error: expected declaration specifiers or ‘...’ before ‘u_int16_t’
xcalib.c:226: error: expected declaration specifiers or ‘...’ before ‘u_int16_t’
xcalib.c:227: error: expected declaration specifiers or ‘...’ before ‘u_int16_t’
xcalib.c: In function ‘read_vcgt_internal’:
xcalib.c:229: error: ‘FILE’ undeclared (first use in this function)
xcalib.c:229: error: ‘fp’ undeclared (first use in this function)
xcalib.c:241: error: ‘u_int16_t’ undeclared (first use in this function)
xcalib.c:241: error: ‘redRamp’ undeclared (first use in this function)
xcalib.c:241: error: ‘greenRamp’ undeclared (first use in this function)
xcalib.c:241: error: ‘blueRamp’ undeclared (first use in this function)
xcalib.c:261: error: ‘SEEK_SET’ undeclared (first use in this function)
xcalib.c:280: warning: incompatible implicit declaration of built-in function ‘malloc’
xcalib.c:300: error: ‘rRamp’ undeclared (first use in this function)
xcalib.c:301: error: ‘gRamp’ undeclared (first use in this function)
xcalib.c:302: error: ‘bRamp’ undeclared (first use in this function)
xcalib.c:379: warning: incompatible implicit declaration of built-in function ‘pow’
xcalib.c:418: warning: incompatible implicit declaration of built-in function ‘malloc’
xcalib.c: In function ‘main’:
xcalib.c:516: error: ‘u_int16_t’ undeclared (first use in this function)
xcalib.c:516: error: ‘r_ramp’ undeclared (first use in this function)
xcalib.c:516: error: ‘g_ramp’ undeclared (first use in this function)
xcalib.c:516: error: ‘b_ramp’ undeclared (first use in this function)
xcalib.c:525: error: expected ‘;’ before ‘tmpRampVal’
xcalib.c:575: warning: incompatible implicit declaration of built-in function ‘exit’
xcalib.c:584: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c:584: error: ‘stdout’ undeclared (first use in this function)
xcalib.c:585: warning: incompatible implicit declaration of built-in function ‘exit’
xcalib.c:805: warning: incompatible implicit declaration of built-in function ‘strlen’
xcalib.c:806: warning: incompatible implicit declaration of built-in function ‘strcpy’
xcalib.c:912: warning: incompatible implicit declaration of built-in function ‘malloc’
xcalib.c:918: error: too many arguments to function ‘read_vcgt_internal’
xcalib.c:926: warning: incompatible implicit declaration of built-in function ‘exit’
xcalib.c:990: warning: incompatible implicit declaration of built-in function ‘pow’
xcalib.c:1022: error: ‘tmpRampVal’ undeclared (first use in this function)
xcalib.c:1034: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c:1072: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c: In function ‘error’:
xcalib.c:1117: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c:1117: error: ‘stderr’ undeclared (first use in this function)
xcalib.c:1122: warning: incompatible implicit declaration of built-in function ‘exit’
xcalib.c: In function ‘warning’:
xcalib.c:1131: warning: incompatible implicit declaration of built-in function ‘fprintf’
xcalib.c:1131: error: ‘stdout’ undeclared (first use in this function)
xcalib.c: In function ‘message’:
xcalib.c:1146: error: ‘stdout’ undeclared (first use in this function)
make: *** [xcalib] Error 1

I've tried putting the xcalib developer package with correct permissions in /usr/bin/ as was recommended in an earlier part of this thread, but I still receive the same message.

---

### Post by jcornuz on 2008-02-09
Hi there,

Looks like you are missing the necessary dev packages to build xcalib. You could start with installing xorg-dev and stuff, but just for xcalib, this is a lot of hassle (trust me :) ). An easier way would be:

If you are on a 32bits architecture, try grabbing the precompiled version here: [http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/xcalib]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/xcalib")

If you are on a 64bits architecture, send me a PM, I have xcalib already compiled.

Take care,

Joel

---

### Post by Zoggy888 on 2008-04-08
Hi Joel,

I'm running Gusty on an Acer Aspire-5315 laptop,  my problem is the color on the TV from the TV-out is way too saturated.  There is a bug report on it:

_[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/174756](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/174756)_

Do you think I could calibrate the TV output using Monica / xcalib from the laptop ?  I don't want to adjust the TV set itself, as this would screw up my regular tv viewing.

Thanks in advance

---

### Post by jcornuz on 2008-04-09
Hi Zoggy,

I am sorry, I don't even have a TV at home and I don't know if / how you can calibrate it. 

I would try to change the saturation either at the xorg level (I am not sure if this is possible) or inside the video/TV playback application - I think this is a better route.

Take care,

Joel

---

### Post by Raven2k360 on 2008-10-24
So I calibrated my monitor's color profile last night in windows and ported it over to Linux and loaded it with xcalib with no issues.  My question now is, is there a way to load the color profile when the system starts up like there is with Windows?  I'd imagine that it will get annoying REALLY fast if I have to manually load the color profile every time I boot into Linux.  Thanks in advance!

---

### Post by AJB2K3 on 2008-10-25
Just to point out ( I've siad it before but) Gimp is a colour aware programme. if you look in the preferences you will find options for setting up input and output profiles.

---

