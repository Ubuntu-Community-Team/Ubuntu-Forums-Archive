---
title: "[SOLVED] Installation - Video Signal Out Of Range"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Jab0rnal on 2008-02-18
Im trying to install 7.10 onto my desktop. When I insert the disk  and boot desktop I get the Ubuntu loading screen as normal. Soon after this I get "Signal out of range" displayed on my monitor.

I know I should be getting the ubuntu desktop and install icon but i just get a monitor in standby.

I have tried the F4 option at the install menu and setting it to 1024x768x16 and some of the other options but i still get the signal out of range issue.

Ubuntu will install with a "Use safe mode for graphics" option install, but after that i can not enable any of the advanced graphics options within ubunto. Any help would be great.

Thank you,
Jab0rnal.

---

### Post by adi_das on 2008-02-18
Install Ubuntu in safe graphics mode and after u install use the visual effects.

---

### Post by Jab0rnal on 2008-02-18
> **adi_das said:**
> Install Ubuntu in safe graphics mode and after u install use the visual effects.

HUH???

As in my previous post.

> **Jab0rnal said:**
> Ubuntu will install with a "Use safe mode for graphics" option install, but after that i can not enable any of the advanced graphics options within ubunto.

By advanced graphic options i did mean the visual effects.

Many thanks,
Jab0rnal

---

### Post by philinux on 2008-02-18
If you have an ATI or Nvidia graphics card then try this site to install the drivers that will enable you to get the effects.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Jab0rnal on 2008-02-18
> **philinux said:**
> If you have an ATI or Nvidia graphics card then try this site to install the drivers that will enable you to get the effects.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

The gfx card is an intel of some sort.

---

### Post by smartboyathome on 2008-02-18
This only happens when Ubuntu tries to boot up with a higher resolution than your monitor supports. If it is a newer card, it may be detecting your monitor size wrong.

Also, is it a widescreen? I found out with enemy territory that monitors don't like to run fullscreen resolutions o a widescreen monitor.

---

### Post by solitaire on 2008-02-18
The error is basically saying the signal produced by the video card is outside the range the monitor can safely handle.

 What exactly is your video card set to when you set the Screen size?

"1024x768x16 ??hz"

Try moving the Hz value to 60Hz or 50Hz and see if you get the same error.

---

### Post by Jab0rnal on 2008-03-03
Hello,

I managed to fix this;

Here is basically what I did:

1.  Installed Ubuntu in safe gfx mode.
2.  Updated Ubuntu to latest available updates.
3.  In a terminal Ran;
```
sudo dpkg-reconfigure xserver-xorg
```
4.  Accepted all defaults apart from the question about letting the Kernel control the hardware, to which i answered 'Yes'.
5.  Rebooted & I can now select different Visual Effects other than 'none'.

Many thanks for all your help;
Jab0rnal.

---

