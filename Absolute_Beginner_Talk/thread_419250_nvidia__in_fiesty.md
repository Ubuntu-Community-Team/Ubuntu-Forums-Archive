---
title: "nvidia ? in fiesty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by l.j. on 2007-04-22
I enabled the nvidia driver in the unsupported control panel when i reboot i just have a black display how can i disable what i did i can get to a command prompt help

---

### Post by mabelrxu on 2007-04-22
try sudo dpkg-reconfigure xserver-xorg-video-all

---

### Post by l.j. on 2007-04-22
No dice, i activated the driver in the administration panel it had me reboot i hear the start up music so its launching just no display can i reverse that or do i need to reinstall  i try to gedit /etc/x11/xorg.conf from terminal says not allowed or something i already had to reinstall from the upgrade to 7.04 i dont want to again any help please

---

### Post by mabelrxu on 2007-04-22
alright ... after start up into ubuntu, do ctrl + alt + f1 and login there ... next, do ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` to backup your current xorg.conf file (srry, but i should've told you to do that before) ... then, do ```
sudo vi /etc/X11/xorg.conf
``` or ```
sudo vim /etc/X11/xorg.conf
``` or ```
sudo nano /etc/X11/xorg.conf
``` or use any other text-editor you like ... finally, find the place where it says "nvidia", probably under the Device section for your video card, and change "nvidia" to "nv" ... also, comment out any weird lines so that your xorg.conf Section "Device" goes from something like this:
```
Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection
```
to something like this:
```
Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
        Driver          "nv"
        Busid           "PCI:1:0:0"
#       Option          "AddARGBVisuals"        "True"
#       Option          "AddARGBGLXVisuals"     "True"
#       Option          "NoLogo"        "True"
EndSection
```

now do ```
sudo /etc/init.d/gdm restart
``` to restart your graphical display manager (gdm) ... hope this helps

oh yeah, and if you do have to reinstall, i suggest putting your /home directory in a separate partition ... makes reinstalling in the future much easier, since you will now get to keep all your files and program settings (as long as you don't mess up and format it by accident :) )

---

### Post by kahrytan on 2007-04-22
While you are at it upgrade to a Nvidia Geforce Fx 5200 or higher. You can nab one for $30-$40 on Newegg.com and It works with the Nvidia driver

---

### Post by Drifter on 2007-04-23
I had the same problem, and I do have an nvidia card higher than 5200.  I got back in by doing what was suggusted and when I got back up I uninstalled the nvidia driver

---

### Post by mabelrxu on 2007-04-24
i'm glad it worked ... :D

---

