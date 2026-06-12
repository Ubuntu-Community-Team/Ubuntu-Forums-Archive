---
title: "Installing ubuntu on intel mac"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by csaldan on 2007-07-09
I just purchased a new MacBook Pro , Intel core 2 duo with the new Nvidia graphics card.

I was wondering if Feisty fawn will work on this one since it is pretty new.

I tried out Ubuntu 6 and it didnt start the xserver, i guess cos of the new nvidia card

could someone give me their views on this

thanks

---

### Post by into_311 on 2007-07-09
I'm not the proud owner of a macbook pro yet...

however, I have heard nothing but good news about getting these to run Linux on them. Especially ubuntu.

It may just be that the graphics card is too new for the open source NV driver to detect?

To get into a working desktop (it will be slow mind you) so that you can get it installed and have a working system temporarily. I would try choosing the failsafe mode when booting off the cd. If that doesn't work, and X won't start, you could try editing the xorg.conf file to use the "vesa" driver and then startx again.  That will at least get you into x server where you can install the software.

At which point, I'm almost certain that the proprietary nvidia-glx driver should know how to detect your new nvidia graphics card though.  To be certain, you could go to:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")

And see if your graphics card is listed in there. That is the latest driver available with Feisty via apt-get.

if it's not listed in there, you could always go with the latest and greatest from Nvidia's site, which might be a lot harder to get installed though:

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

and see if your graphics card is supported by the latest release from Nvidia.

Another thing that comes to mind, is if you are using the Broadcom wireless card in that Macbook, you may encounter some difficulties here and there with that. This is mostly due to the broadcom not releasing any specs/open drivers for hteir products. THe community is making a very strong effort to try and reverse engineer a driver, but its not there 100% yet (I would say).

---

### Post by stchman on 2007-07-09
> **csaldan said:**
> I just purchased a new MacBook Pro , Intel core 2 duo with the new Nvidia graphics card.

I was wondering if Feisty fawn will work on this one since it is pretty new.

I tried out Ubuntu 6 and it didnt start the xserver, i guess cos of the new nvidia card

could someone give me their views on this

thanks

I believe Ubuntu makes a distro for Intel based Macs.

---

### Post by csaldan on 2007-07-09
its NVIDIA GeForce 8600M GT

---

### Post by csaldan on 2007-07-13
[http://ubuntuforums.org/showthread.php?t=474144&highlight=csaldan](http://ubuntuforums.org/showthread.php?t=474144&highlight=csaldan)

Check out this link if anyone is having a problem with the new MBP santa rosa

---

