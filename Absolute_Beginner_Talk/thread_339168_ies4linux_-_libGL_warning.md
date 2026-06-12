---
title: "ies4linux - libGL warning"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mygravity on 2007-01-15
Hi there,

Have installed the Edgy Eft and need to install IE 6.0 for web development. Unfortunately ies4linux hangs at the stage "Creating Wine Prefix" with the following error:

libGL warning: 3D driver claims to not support visual 0x4b

Could anyone please advise me on how to fix this error?

I have a Matrox Millenium G400 agp graphics card with 16MB RAM. Attached is my xorg.conf for reference.

Many thanks

Andrew

---

### Post by The Joe on 2007-01-15
Did it stop the install? I've had this a couple of times running Wine and it hasn't actually caused any problems.

---

### Post by mygravity on 2007-01-15
Hi,

Yes, it completely stopped the install. I left it hanging for about 10 minutes and nothing happened so I did a Ctrl-C to stop it. No desktop icons are created, and there aren't any executables in ~/.ies4linux.

Thanks for the response!

Andrew

---

### Post by Thomas Rasmussen on 2007-01-17
Hi, Just had the exact same experience on Ubuntu 6.10 and latest wine available from winehq (or the site where it links to). No matter what I tried, it gave the same error.
I tried to comment the line loading module GLX in xorg.conf and that actually solved the problem, so now I can fire up both normal winecfg (it failed too!) and ies4linux. I'm running with a Matrox G550 card, so it seems there is a bug in either the mga GL driver, wine gl interface or something else?

The only problem is that Wine complains about missing OpenGL when starting applications, but it works fine (guess performance is worse without GL?)

Thomas

---

### Post by The Joe on 2007-01-17
I can only really think it's your graphics card driver. I'm no expert with drivers, they always give me a headache. What I would suggest is to try to reinstall your driver or update it. I'm sorry I can't help more than that.

Ah! Wait hang on, do you even have Wine installed?

---

### Post by Thomas Rasmussen on 2007-01-18
> **The Joe said:**
> I can only really think it's your graphics card driver. I'm no expert with drivers, they always give me a headache. What I would suggest is to try to reinstall your driver or update it. I'm sorry I can't help more than that.

Ah! Wait hang on, do you even have Wine installed?

I agree it is probably the graphics card driver that is buggy... Wine is certainly installed, it is wine that writes the 'creating wine prefix' text. Also, after I commented the GLX module in xorg, everything works like a charm. 

Thomas

---

### Post by Thomas Rasmussen on 2007-01-18
Though I hate to answer my own posts, this is what I have found on the net:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)
[https://launchpad.net/ubuntu/+source/wine/+bug/64705](https://launchpad.net/ubuntu/+source/wine/+bug/64705)

which apparently suggests that putting
Option "UseFBDev" "true"
in your Device section for your gfx card will solve the problem. I haven't tested it yet (as I'm not near my computer) but I sure will have a go at this when I get home. It also seems that it is caused by some upgrade of the mga gfx driver, but I haven't searched that much for it, so I don't know if there is a fix or if the 'real' solution is the UseFBDev solution.

Thomas

---

### Post by Thomas Rasmussen on 2007-01-18
OK, now I've read a bit about it, and tried to suggested things, however that didn't help anything. However I tried (for fun) to install the latest xorg-xserver-video-mga package from debian unstable (version 1.4.4) and with this installed (actually only unpacked as it won't install correctly due to dependencies) I got it working.
I then copied the new file (/usr/lib/xorg/modules/drivers/mga_drv.so) to a backup directory, reverted to the original ubuntu package (found it on the server) and then copied my backup driver (the new one) back into the directory. Then restarted X and now it is working more or less (it still comes with the warning, but it doesn't freeze).

Furthermore I have discovered that this has absolutely nothing to do with wine, but rather the 3D stuff in the driver. With everything native, I couldn't even run glxinfo, it also gave the same message and froze up. With my little driver-hack, I can run both glxinfo and the glx-demo programs (glxgears etc).

Thomas

---

