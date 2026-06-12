---
title: "error in beryl"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-03-26
when I type beryl in the terminal the following appears:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap


any help in fixing this ?

I'm running kubuntu 6.10 edgy eft and a graphics card nvidia 6200 GeForce

and if this appeared in any post before please post the link

many thanks to those who help out

---

### Post by Waappu on 2007-03-27
Hi

Try use envy to install video driver and let it configure your xorg.conf
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by skidkid87 on 2007-03-28
it didn't work 

it actually messed up the nvidia settings that I had leading for the GUI not to work and I went through hell to get it back again and the I still get the message above now

but thnx anyways

---

### Post by Bazzaah on 2007-03-28
you could check this guide out, but bear in mind that it's for ATI cards so you need to make sure that you use nvidia drivers. I don't know whether the installation process for nvidia drivers and beryl is different from the prodcedure you would follow for an ATI card, but if nothing else if might give you an idea about where to go next.

Might be worth checking in at the beryl forums as well.

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

