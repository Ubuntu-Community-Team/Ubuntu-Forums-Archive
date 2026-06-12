---
title: "Nvidia Drivers"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Dandalf on 2008-01-23
I'm having trouble installing nvidia-glx-new. They show as installed in the package manager, but when I go to enable restricted drivers, only the nvidia display driver, NOT the nvidia NEW driver, is available to activate. If I activate and reboot, my computer will go into low graphics mode an I have to default my xorg and start again. I've tried envy, but that gives me an error about not having dependencies or something. Halp

---

### Post by philinux on 2008-01-23
From posts on here people seem to use ENVY.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by skymera on 2008-01-23
i used Envy, it is very good.

highly recommended.

---

### Post by rhc on 2008-01-23
> **Dandalf said:**
> I've tried envy, but that gives me an error about not having dependencies or something. Halp

Or something? It's important that what is the something?

---

### Post by skymera on 2008-01-23
whats your sources.list?

cat /etc/apt/sources.list

---

### Post by Dandalf on 2008-01-25
Thanks for the fast replies guys! Sorry I wasn't here on the same day, had to go out. Didn't count on such quick responses! :) Let me answer your helpful questions here

> **skymera said:**
> whats your sources.list?

cat /etc/apt/sources.list

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
deb http://blognux.free.fr/debian unstable main
deb http://archive.canonical.com/ubuntu gutsy-commercial main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
#AUTOMATIX REPOS END
```

> **rhc said:**
> Or something? It's important that what is the something?

Ok, first I start envy. On the main front end I first click 'Uninstall the Nvidia Driver' to make sure I have a clean system.

Then, without restarting, I click 'Install the Nvidia Driver', and watch the console output.

The end message I receive is

'module-assistant error message

Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use'

Now when I next reboot, I'll have to select default graphics mode for xorg, then reboot again and use xorg-xserver-reconfigure to get back to my native 1680x1050 resolution so I can use ubuntu comfortably. My display drivers will remain inactive :(

edit: before rebooting however, i've checked my synaptic, and it lists nvidia-glx-new as a broken package. Perhaps envy tried to install it and failed half way? What if I install it manually, how do I 'activate' it? I've tried this before, but when installing it manually it doesn't appear in restricted drivers manager - only the old 'NVidia accelerated graphics driver' is there, and IIRC that's not glx-new, although I'm not sure.

I've never tried the 'Install Nvidia Driver Manually' option in ENVY.

Thanks again for all the help guys :)

---

### Post by hyper_ch on 2008-01-25
You konw tht automatix is not recommended?

---

### Post by Dandalf on 2008-01-25
I guess all I really need to know is, once I've installed nvidia-glx-new in synaptic, how do i 'enable' it? It doesn't appear in restricted drivers manager, so how do I do it 'manually' ?

---

### Post by funrider on 2008-01-25
bro i got similar problem like you yesterday after installing virtualbox and messing up with some package. struggled for hours and finally did an OS reinstall. 

if you are using 7.10, it should recogize your nvidia card and will ask if you want to enable it once the OS started up from a new installation. i am glad that i didnt have much stuff to backup. if you are in similar situation, reinstall it bro

---

### Post by Dandalf on 2008-01-28
Surely someone can tell me how to manually enable my nvidia-glx-new ? I'm not installing the whole operating system just because I can't get the display drivers installed. Windows users would laugh!

---

### Post by Therion on 2008-01-28
See if [THIS]("http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/") helps??

---

### Post by r4ik on 2008-01-28
I would create a "clean" sources list do a update and upgrade and try Envy again.

sudo gedit /etc/apt/sources.list

   

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

