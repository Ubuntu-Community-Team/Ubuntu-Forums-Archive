---
title: "Wrong colors in games"
date: 2013-01-23
forum: Apple Hardware Users
---

### Post by xeno74 on 2013-01-23
Hi,

I've installed Linux on my Power Mac G5 2003 (Radeon  9600 128 MB VRAM). I use the KMS/Gallium 0.4 driver for 3D acceleration.  3D works but I have wrong colors inside SuperTuxKart 0.8.

I don't have a xorg.conf but in the yaboot.conf the follwing line:

```
append="video=radeonfb:off radeon.modeset=1"
```Any tips?

Cheers,

Xeno

---

### Post by xeno74 on 2013-01-24
I've solved the conflict with fb driver with

/etc/yaboot.conf

```
....

append="video=radeonfb:off radeon.modeset=1 video=offb:off video=1280x1024-32"

....
```but the problem with the wrong colors isn't solved :(

A new screenshot: [http://s4.imgload.info/yz74kd15u569jyb.png](http://s4.imgload.info/yz74kd15u569jyb.png)

What can I do?

---

### Post by rsavage on 2013-01-25
Have you thought about contacting the debian powerpc mailing list ([http://lists.debian.org/debian-powerpc/](http://lists.debian.org/debian-powerpc/) ) and seeing if you can catch the eye of somebody like Michel Danzer?
 
I have a problem with KMS in Lubuntu - the window title bars are the wrong colour. I have a different radeon card to you though.  Also cairo-dock can give messed up colours  (non-KMS), but if you change the theme to one that uses a different picture format it can help.
 
Sorry can't be much more help.  If you were using non-KMS then I'd suggest playing around with the GART settings.

---

