---
title: "stupid question but...[dvd playback]"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-08
i know its a rather noobish question, but how do i get dvds to play in fiesty fawn?i am wondering what gnome/gstreamer packages are needed, cause when i try to play a dvd on my computer[yes it does have a dvd drive] i get this>[IMG]http://99bluefoxx.deviantart.com/art/0001-71620067[/IMG]
and>[IMG]http://99bluefoxx.deviantart.com/art/0002-71620261[/IMG]
i have most of the gstreamer codecs i could find installed, so what am i missing? is there a terminal command that will list packages[i would guess ```
lssources
```or something...]
any help is good help
oh and also, i tried to play the dvd with mplayer, and rip it with thoggen, both failed as well[thoggen crashed my desktop infact, i tried again in KDE]

EDIT: im not sure whether the images i tried to insert are showing up, i personally cant see them so ill attach them

---

### Post by awthomp on 2007-12-08
Check out the medibuntu packages found here:

[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by 99bluefoxx on 2007-12-08
so i tried what was here [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)
and this is the result from this ```
bluefoxx@azurE-prIDE:~$ sudo apt-get install gxine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3

```
this is the result of that
```
bluefoxx@azurE-prIDE:~$ sudo apt-get install gxine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
bluefoxx@azurE-prIDE:~$


```

i checked the softwear sources, and all are enabled, and i reloaded them, but no different
so now what?

---

### Post by gupta_sumesh63 on 2007-12-08
libdvdcss2 is in repositories for Gutsy and not for feisty. Please google for it and install it from other site. or there is a provision in libdvdread3 or usr folder to install it. I am really sure about it. Google should be better option. Also download w32codecs. They should be available in repositories.

---

### Post by fulllefty on 2007-12-09
> **gupta_sumesh63 said:**
> libdvdcss2 is in repositories for Gutsy and not for feisty. Please google for it and install it from other site. or there is a provision in libdvdread3 or usr folder to install it. I am really sure about it. Google should be better option. Also download w32codecs. They should be available in repositories.

I have download this w32codecs package from medibuntu, [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)

when I try to install (using Debi / GDebi, i don't remember the program name exactly) on my feisty, there are missing dependencies libc6, actually in Synaptic the libc6 is already installed.
So why the "missing dependencies" thing happen? :confused:
Are the package meant for Gutsy Release only?:(

---

