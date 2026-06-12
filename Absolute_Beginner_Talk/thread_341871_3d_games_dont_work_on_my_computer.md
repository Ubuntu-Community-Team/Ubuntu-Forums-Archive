---
title: "3d games dont work on my computer"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-01-19
i downloaded Warsow, Scorched, and Armagetron and some other 3d games on my computer, and non of them seem to work.  The only one that gave a hint that it was trying to work was "scorched 3d" and it gives an error which says
*******************************************************
The Scorched3d process terminated due to configuration errors.
Display : ERROR: Failed to set video mode.
Error Message: Couldn't find matching GLX visual
----------------------------
Requested Display Mode:-
Driver=x11
Resolution=640x480x0 (windowed)
DepthBuffer=24
DoubleBuffer=On
ColorComponentSize=0

Scorched 3D Display : ERROR: Failed to set the display mode.
Ensure that no other application is exclusively using the graphics hardware.
Ensure that the current desktop mode has at least 24 bits colour depth.
***********************************************************
The others dont even give a hint that it processes anything after i select the game (like Armagetron).  Warsow was the first game i tried, and i Deleted it bcos i was bcoming frustrated trying to make it work.

The funny part is that i dont see any list of requirements that we need prior to downloading the game.  Or maybe i dont understand what they are talking about.

So is there anybody that can help me get at least Scorched to work, then i move to another.

---

### Post by scrooge_74 on 2007-01-19
You probably dont have 3D acceleration enable.  What video card do you have? You probably need to install the correct drivers to be able to play does games.

Example, I have an Nvidia card, things were either very slow or will not work until I installed the correct drivers, Ubuntu has open source drivers for my card but it does not support 3D, I had to download the correct set from Nvidia

---

### Post by BarfBag on 2007-01-19
You need to install your graphics driver so you can get 3D acceleration.  If you have an nVidia card, you're in luck - their drivers are amazing.  The ATI drivers aren't as good, but they get the job done.

[Here's nVidia instructions.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")
[Here's ATI instructions.]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

### Post by RomeReactor on 2007-01-19
To know if 3d acceleration is the issue, open a terminal (Applications-->Accessories-->Terminal), and write:

```
glxinfo | grep direct
```

should say yes if you do have 3d acceleration. Also post which card you have, please.

---

### Post by darkchest on 2007-01-19
i have a nivdia card.  I am trying to follow the instructions that Barfbag gave.  I hope it would work....If it doesnt, i would post the result.

---

### Post by xpod on 2007-01-19
The drivers from here are a good bet

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

Should make life a bit simpler mabey?

---

### Post by darkchest on 2007-01-19
I got scorched to work, but the resolution of my screen is bigger than usual.  It is 640 x 480, and that is the only option given.  How can i correct this?

---

### Post by davebgimp on 2007-01-19
> **darkchest said:**
> I got scorched to work, but the resolution of my screen is bigger than usual.  It is 640 x 480, and that is the only option given.  How can i correct this?

Check /etc/X11/xorg.conf and see what resolution options you have and what is currently selected as the default.

---

### Post by dlyte on 2007-01-19
> **darkchest said:**
> I got scorched to work, but the resolution of my screen is bigger than usual.  It is 640 x 480, and that is the only option given.  How can i correct this?

Go into applications, accessories, resolution switcher. that should work. If not, go into your nvidia x server settings in the system tools menu or ATI configure menue under applications. If that doesnt work you can add it in your xorg.conf file located in /etc/X11/xorg.conf. in order to access it though you need to go to the terminal window and type sudo gedit /etc/X11/xorg.conf and add the resolution you want under screen. Or if you have not installed a driver the easiest way is to type this. hold ctrl and alt an hit number 2 and log in. then type sudo dpkg-reconfigure -phigh xserver-xorg then hit space bar on the resolution you want.

hope one of those helps

---

### Post by darkchest on 2007-01-19
i have installed the nvidia driver.  and under Section "Screen" of /etc/X11/xorg.conf, i see
********************************
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "VG150"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "720x400" "640x480"
    EndSubSection
.......
*******************************
It seems that the 3 options are available, but it doesnt show in the System>Preference>Screen Resolution

Also, i dont know where to locate the Nvidia x server settings.  I have installed the nvidia driver, so i DONT know if i should do what u said DLYTE.

DLYTE:  "Or if you have not installed a driver the easiest way is to type this. hold ctrl and alt an hit number 2 and log in. then type sudo dpkg-reconfigure -phigh xserver-xorg then hit space bar on the resolution you want."

---

### Post by dlyte on 2007-01-20
The nvidia x server should be under applications, system tools, and nvidia x server settings. or something like that. You might also want to try envy. its a great nvidia driver installer. here is the website for envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) scroll down to untill you find 

envy_0.6.1-0ubuntu2_all.deb and click on it. the it will install envy. then all you need to do is hit ctrl alt and F2 at the same time log in and type envy 
then uninstall nvidia driver and and follow the steps its super easy. then after that do a re-install and it will install the latest drivers and give you the best resolution  settings. then you can go into  the applications, system tools, and nvidia x server settings. 

hope that works

---

