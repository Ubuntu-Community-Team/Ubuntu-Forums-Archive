---
title: "nVidia Drivers"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2007-05-02
Hey all, 
I have an nVidia card (and the correct drivers from nVidia)
But...uh...
What should I type into the Terminal to install it? I tried to just install the one in the repository, but I think I need to use the correct drivers, as I can do everything EXCEPT rendering. 
I just need to know how to make everything right. 
Cheers, 
Mr. Psychopath

---

### Post by starcraft.man on 2007-05-02
[Envy]("http://www.albertomilone.com/nvidia_scripts1.html") enter Stage left.

Great program, I still direct people to it :).

Simple to use, read the notes at the top of the home page and then get the 0.9.2 debian installer. Install the program, go to Applications > System Tools > Envy and then choose Automatically Install Nvidia Driver.

Then just follow the prompts, say yes if it asks for anything during the install, and after say yes to reconfigure xorg and reboot. Then you should be done.

Have a nice time :)

---

### Post by Nythain on 2007-05-02
what version of ubuntu are you using... in feisty its as easy as 
```

sudo apt-get install nvidia-glx(or nvidia-glx-new, depending on your card) nvidia-kernel-common

```
then edit your xorg.conf a wee bit, namely change:
Section Device
Driver "nv"
to
Driver "nvidia"

also installed is a great tool for configuring the card with a gui
```

gksudo (or kdesu) nvidia-settings

```

as for manually installing the .run package downloaded from nvidia, its a bit trickier... make sure you are logged out of your desktop environment and at a command line...
```

    sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
    sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
    sudo rm /etc/init.d/nvidia-*
    sudo /etc/init.d/kdm stop (or gdm for gnome users)
    sudo ln -sf /bin/bash /bin/sh
    sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run (where XXXX is the driver version you downloaded)
    sudo ln -sf /bin/dash /bin/sh

```

reboot and that should work... hopefully... thats almost a step by step guide that i wrote for myself to follow everytime i reinstalled them in edgy...

---

### Post by DeadSuperHero on 2007-05-05
Erm, question:
where's my xorg.conf file at, is it under the shared folder?

---

### Post by Outrunner on 2007-05-05
/etc/X11/xorg.conf

Assuming you have gedit insalled:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by DeadSuperHero on 2007-05-05
Wow, thanks!
This is why I love this community. Everyone's so quick to help!

EDIT: Well, still no luck quite yet. I'm doing everything manually now, and it asks me this:

> The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2346kB of archives.
After unpacking 8839kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.


Is that supposed to happen, or am I all done?

---

### Post by DeadSuperHero on 2007-05-05
I'm, like, totally confused. I really want to get everything to work. Whenever I start any of my 3D stuff, it tends to start up, load everything, then crash. Maybe I picked the wrong driver...

---

### Post by DeadSuperHero on 2007-05-12
Well, I've got everything working terrifically now. I just took out the card booted up, turned off, and put it back in.
Hey, how do I tell Ubuntu to automatically run Beryl and gDesklets every time I log in?

---

### Post by starcraft.man on 2007-05-12
> **Mr. Psychopath said:**
> Well, I've got everything working terrifically now. I just took out the card booted up, turned off, and put it back in.
Hey, how do I tell Ubuntu to automatically run Beryl and gDesklets every time I log in?

System > Preferences > Sessions.

Push add, and then you can set any terminal command to execute at startup.

Then just add their commands, its "berly-manager" and I think "gdesklets". Thats it, easy huh? :)

Have fun with Beryl.

---

