---
title: "Full Resolution problems on Macbook Pro"
date: 2007-06-24
forum: Apple Intel Users
---

### Post by xelapond on 2007-06-24
Hi, I have a first gen, 15 inch macbook pro that I just installed ubuntu linux on.  Everything has worked great so far, except the screen resolution.  The pro is supposed to be able to handle a 1440 by 900, but all Ubuntu will give it is 1024 by 768.  This is not even widescreen, so on top of being all pixelated it is skewed.  Does anyone know how to get a 1440 by 900 resolution on this thing?  I might have to switch back to Mac OS X if I cannot get this to work:(

Alex

---

### Post by ivesjd on 2007-06-24
Can you tell us some info on the laptop? Like what version MBP it is? The newer ones have the NVIDIA graphics card and the older ones have the ATI card. But you might just need to go into System>Prefrences and select the restricted drivers manager and install the video drivers that it has listed.

---

### Post by ronocdh on 2007-06-24
> **xelapond said:**
> Hi, I have a first gen, 15 inch macbook pro that I just installed ubuntu linux on.  Everything has worked great so far, except the screen resolution.  The pro is supposed to be able to handle a 1440 by 900, but all Ubuntu will give it is 1024 by 768.  This is not even widescreen, so on top of being all pixelated it is skewed.  Does anyone know how to get a 1440 by 900 resolution on this thing?  I might have to switch back to Mac OS X if I cannot get this to work:(

Alex
Have you confirmed that you are indeed running the propriety ATI driver (fglrx) by checking the Restricted Drivers Manager as ivesjd mentioned? If you are, this command will let you declare the 1440x900 resolution, adding it to your Screen Resolution preference panel:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If you are not running the fglrx driver... then I think you could not be posting. :D But let us know if that's the case.

---

### Post by xelapond on 2007-06-25
I have a first gen:

1Gb ram
80Gb HD
128Mb ATI X1600
DVD Burner
Core Duo 2.0 Ghz

In the restricted drivers manager it says ATI Accelerated graphics driver

when i run sudo dpkg-reconfigure -phigh xserver-xorg it does not let me pick 1440 by 900, or it does but does not change anything...

Any other suggestions?

---

### Post by ronocdh on 2007-06-25
> **xelapond said:**
> when i run sudo dpkg-reconfigure -phigh xserver-xorg it does not let me pick 1440 by 900, or it does but does not change anything...

Any other suggestions?
When you highlight that resolution (with arrow keys), press the spacebar to add an asterisk beside it, thereby declaring it as a desired resolution.

---

### Post by xelapond on 2007-06-25
When I run that command it does not even acknowledge thatsudo dpkg-reconfigure -phigh xserver-xorg I did anything.  I select the fglrx driver, then 1440 by 900 and it just ignores it.  When I run the command again it looks that same as it did the first time.  It has VESA selected and only 1024 by 768, 800 by 600 and 640 by 480.

Am I missing something again?

Also, would my changes let m change the resolution to 1440 by 900 in the Pref window, or terminal?

---

### Post by ivesjd on 2007-06-25
> **xelapond said:**
> When I run that command it does not even acknowledge thatsudo dpkg-reconfigure -phigh xserver-xorg I did anything.  I select the fglrx driver, then 1440 by 900 and it just ignores it.  When I run the command again it looks that same as it did the first time.  It has VESA selected and only 1024 by 768, 800 by 600 and 640 by 480.

Am I missing something again?

Also, would my changes let m change the resolution to 1440 by 900 in the Pref window, or terminal?

I'm not sure, but the command I run for this is ```
sudo dpkg-reconfigure xserver-xorg -phigh
``` I'm not sure if that'll help.

---

### Post by ronocdh on 2007-06-25
> **ivesjd said:**
> I'm not sure, but the command I run for this is ```
sudo dpkg-reconfigure xserver-xorg -phigh
``` I'm not sure if that'll help.
I apologize if I have the modifier wrong. Try how Ivesjd has phrased it, then just try:
```
sudo dpkg-reconfigure xserver-xorg
```
That is the command I always use when setting up; AIUI, the **-phigh** modifier lets you skip all the keyboard stuff and just focus on the graphics.

---

### Post by xelapond on 2007-06-25
Thanks, that worked, i know have it at 1440 by 900.

Alex

---

