---
title: "Lubuntu 12.04 PPC on iMac G5, black screen with cursor"
date: 2013-03-08
forum: Apple Hardware Users
---

### Post by darkpepe on 2013-03-08
Hi,

I'm booting off a usb drive with the option "live b43.blacklist=yes" (else I get stuck at the message, isight failed loading firmware).

I get past the splash screen up to the point where I can move the mouse cursor (very sluggish) on a black background but can't get anywhere else, not even ctrl+alt+F1.

I tried radeon.modeset=0 video=radeonfb:1024x768-24@60 noveau.noaccel=1 with no difference (It's a X600 with RV380 chip).

Any advice very welcome!

Thanks!

---

### Post by darkpepe on 2013-03-12
Bump.

I was able to install Lubuntu with alternate installer. Same problem at boot as live version, but at least I can get into console with ctrl+alt+F1.

Surprisingly, I noticed there is no xorg.conf file at /etc/X11 o_O. Anyone with an "iMac G5 iSight" that can advice?

Thanks

---

### Post by rsavage on 2013-03-12
Update your kernel.  Then reboot with video=ofonly to see if KMS works.  If not, then you should be able to use the fbdev driver to get you at least started.

---

### Post by darkpepe on 2013-03-12
To update the Kernel, is apt-get dist-upgrade good enough?
Thx!

---

### Post by rsavage on 2013-03-12
Yep, that'll do it.  It will update everything, so will take a bit of time.  To just do the kernel it would be:

sudo apt-get install linux-image-powerpc64-smp

With KMS you may have to reduce your apgmode.  For example, radeon.agpmode=1 or even radeon.agpmode=-1 (pci mode).

---

### Post by darkpepe on 2013-03-14
Hi again, sorry for the delay replying.
The setting "video=ofonly radeon.agpmode=-1" on boot ends up in a blinking text cursor in the upper left corner.

I  created manually a xorg.conf file inside /etc/X11 which yielded more  success. Now I get to the login screen of Lubuntu, but I'm stuck in a  loop. After typing in the password, the desktop seems to load but I just  get the login screen again :(

Any ideas?

Thx!

---

### Post by 60six on 2013-03-15
Having same probs as you darkpepe, although when I get just the mouse cursor if I type my password and hit enter - it goes into ubuntu, albeit the extra-low res version. I have ran apt-get dist-upgrade from there - will tell you how it goes.

---

### Post by darkpepe on 2013-03-15
Well,I was already able to upgrade from terminal (ctrl+alt+F1). I also get full resolution after creating xorg.conf file,  but I'm stuck with the loop at login screen....
Will post xorg log next Tuesday when I'm back.

---

### Post by gusduenas on 2013-03-15
ubuntu 12.04 alternate cd installs pretty good onto a mac ppc g5 early 2006 dual 2.0ghz nvidia geforce 6600 256mb...problem with the graphic card, but still working on that.

---

### Post by gusduenas on 2013-03-15
When  I say problem that means you can boot into ubuntu 2d with great graphics...don't misunderstand me

---

### Post by gusduenas on 2013-03-15
by the way how can I create a xorg.conf file for an nvidia geforce 6600? thanks.

Gus

---

