---
title: "Hardware Acceleration."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by jay6 on 2006-10-15
I searched, searched, napped, searched, and then searched some more...I found multiple threads on the forum about Hardware Acceleration, but all were (sadly) to complicated for my lack of Kubuntu knowledge. 

Goal: Get 3d desktop working.

Troubles: No hardware acceleration...These are the steps I have taken, to attempt to see how to "accelerate" all the graphic card crud...

Typing in flgrxinfo into konsole and I receive..
___
jay@jay-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
____

Oh joy...So then I also type.
____
jay@jay-laptop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied   ----> Darn permissions...
jay@jay-laptop:~$ sudo /etc/X11/xorg.conf
Password:
sudo: /etc/X11/xorg.conf: command not found
jay@jay-laptop:~$
____

Keep in mind I am a complete idiot when it comes to all Kubuntu things..So I just tried sudo because I have seen other people do it for administrator things...

So, then I type (which I know verifies I don't have hardware acceleration)
____
jay@jay-laptop:~$ glxinfo |grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
____

So, also being an beginner, I have no idea as to where to find what Graphics Card I have..I looked in system Settings, and got nothing. I forget how, but I found something a while ago that said something about Versa, or Vera or something comparable...

In THIS thread [http://ubuntuforums.org/showthread.php?t=180097&highlight=hardware+acceleration](http://ubuntuforums.org/showthread.php?t=180097&highlight=hardware+acceleration) Fass said to get the fgrlx driver, so, well, I go to adept and get it..Now what...

Anyway, hopeless and lost I figured I'd just start a new thread out of hundreds, hoping that I will magically get a kind soul who will say "Do this: explanation" instead of "do this:"...

I have an Acer Aspire 5000 laptop, if that'll help anyone..

Thanks in advance!

---

### Post by pay on 2006-10-15
Not /etc/X11/xorg.conf or sudo /etc/X11/xorg.conf use ```
sudo nano /etc/X11/xorg.conf
```or ```
gksudo gedit /etc/X11/xorg.conf
``` and it isn't vera, it's vesa. When you open up your X11 it will have information about what video card you have.

---

### Post by jay6 on 2006-10-15
Well, thanks for the correction with Vesa, however, I still would appreciate much help with where to start or what to do with accelerating my hardware...I have no idea what to do with gksudo gedit /etc/X11/xorg.conf or the other option...

---

### Post by igknighted on 2006-10-15
Do you know what brand your graphics card is?  It sounds to me like an ATI card, and if it is, to enable DRI you need to install the ATI prop. drivers, not the mesa ones.  Open a terminal and type:

```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

**warning**: only do this if you do in fact have an ati card

after you have done this reboot your computer and then try fglrxinfo and DRI should be enabled and it should say ATI - [your card] and not mesa

---

### Post by xpod on 2006-10-15
What "3ddesktop" are you talking of??
The basic one in synaptic\adept or the beryl\compiz stuff???

I had the basic one running on a basic onboard graphics then after installing a new nvidia card the other day now have the "beryl" stuff running on my kubunto desktop but it still wont play on the ubunto.

---

### Post by PriceChild on 2006-10-15
If you definately do have an ATI card, follow [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver) to install the drivers.

---

### Post by jay6 on 2006-10-15
Alright, so, if possible, in a nice 1.2.3 step method could someone tell me how to find out what graphics card I have?

And if I do have this ATI card, thanks for the responses!!

I am trying to get the 3d desktop that adept finds when you type "3ddesktop"...

---

### Post by pay on 2006-10-16
Open the terminal type ```
sudo nano /etc/X11/xorg.conf
```and it will say what video card you have. (I think that it is under device). Look for Ati, Nvidia, Intel, Voodoo, Savage...

---

### Post by CatKiller on 2006-10-16
```
lspci | grep VGA
```should tell you what your graphics card thinks it is.

---

