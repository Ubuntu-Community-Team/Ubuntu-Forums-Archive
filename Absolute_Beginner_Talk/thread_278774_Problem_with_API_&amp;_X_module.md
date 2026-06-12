---
title: "Problem with API &amp; X module"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by ripped_up on 2006-10-16
I tried installing the nvidia graphics driver from the nvidia site. I used the guide from this thread [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

Now I get this error:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7174,
but this X module has the version 1.0-8774. Please make sure that the 
kernel module and all NVIDIA driver components have the same version.

Now I can only get to a command prompt in recovery mode, so I try sudo apt-get install nvidia-glx and it installs the driver.

Now I get error:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8762,
but this X module has the version 1.0-8774. Please make sure that the 
kernel module and all NVIDIA driver components have the same version.

How can I resolve this issue so I can get back into KDE? I am a total n00b so please give instructions step by step. Thanks.

---

### Post by blendmaster on 2006-10-16
This may or may not work, but try

```
startx
```

on the command prompt.

This could get you back into GNOME in a really bad looking environment, but this doesn't always work. If it does, It'll be easier to fix this problem.

If you manage to get back into x, try going [here]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38") (the automatix site) to install a program called automatix. This program will install x drivers automatically for you.

Again this may not be of much help to you. Good luck! :-D

---

### Post by ripped_up on 2006-10-16
Thanks but no go. X pukes out and gives that error.

---

### Post by blendmaster on 2006-10-16
Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

By the way, this is another one of those "May or may not work..."

Sorry I can't help more. ;)

---

### Post by ripped_up on 2006-10-16
> By the way, this is another one of those "May or may not work..."

Sorry I can't help more. 

Any help is greatly appreciated! 
I tried it with no luck.

---

### Post by blendmaster on 2006-10-16
The how-to has you uninstalling nvidia-glx, try:

```
sudo apt-get install nvidia-glx
```

I don't know if this'll help that much.

After installing, then try startx, by the way, I remember once I had to type startx twice to get it going, but I'm doubting this'll work for you.

---

### Post by blendmaster on 2006-10-16
Also edit /etc/X11/xorg.conf by:

```
sudo nano /etc/X11/xorg.conf
```

and change the lines under modules:

```
Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#Load "dri"
#Load “GLcore”
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
```

to:

```
Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load “GLcore”
Load "extmod"
Load "freetype"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
```

and change this:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
```

(the part that says "nvidia") to "nv".

Hope that helps!

---

### Post by ripped_up on 2006-10-16
blendmaster, making those changes to xorg.conf got me back into KDE and I was able to fix the problems. Thanks for your help!

---

### Post by irlandes on 2007-01-28
that solution worked by getting rid of nvidia and using nv.  If anyone faces this problem, check to see if you have a file /etc/default/linux-restricted-modules.

This file will itself explain what is happening.  By default, the different module is being loaded though you are installing the new module.  Clearly, that conflicts. Some say to purge restricted modules,but the fast fix is to change the last line of this file to:

DISABLED="nv"

Save it and your nvidia driver will work as soon as you change that nv in the xorg.conf file back to nvidia.

---

