---
title: "enabling display effects"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by _anant on 2008-01-20
dear friends,
my graphics card is:nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
graphics card driver:nvidia-glx-legacy
monitor:acer 19" wide [Acer AL1916W]

i cannot enable even normal display effects.I have also tried manually installing the driver specified by nvidia but even that does'nt work.I have tried changing my xorg.conf file  "nv->nvidia".
even this does'nt work:( !What am i suppose to do?Help

---

### Post by Kosimo on 2008-01-20
> **_anant said:**
> dear friends,
my graphics card is:nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
graphics card driver:nvidia-glx-legacy
monitor:acer 19" wide [Acer AL1916W]

i cannot enable even normal display effects.I have also tried manually installing the driver specified by nvidia but even that does'nt work.I have tried changing my xorg.conf file  "nv->nvidia".
even this does'nt work:( !What am i suppose to do?Help

What OS are you running? Ubuntu 7.10 Gutsy?  Did you try using restricted drivers?
Did you try envy?

---

### Post by rosegarden78 on 2008-01-20
> **Kosimo said:**
> What OS are you running? Ubuntu 7.10 Gutsy?  Did you try using restricted drivers?
Did you try envy?

Yes ... please consider navigating to User CP and updating which Ubuntu you use.  It may  increase the speed and quality of our feedback.  I've use the eye candy.  I hate it.  It gives me headaches.  I use an XCFE system with GNOME and KDE and I run Nautilus on top of Xubuntu.  I have no use at all for display effects - only speed, power and simplicity.

That said - those effects are included in Ubuntu by default as of Gutsy Gibbon 7.10.  I suggest trying the latest version.  

Feisty and Edgy MAY crash frequently with visual effects enabled but *not* Gutsy.

---

### Post by _anant on 2008-01-20
i m using gutsy 7.10
i have installed compiz .I ve updated the system and installed compiz from synaptic

---

### Post by _anant on 2008-01-21
my graphics card is not blacklisted
however it is in the restricted drivers list

---

### Post by Sbarton on 2008-01-21
Have you tried enabling your card in 'System-Administration-Restricted drivers manager.
Select your card and enable it.
regards

---

### Post by _anant on 2008-01-21
i have enabled the card already

---

### Post by torgrot on 2008-01-21
That card is pretty old.  If you can get effects enabled, I am pretty sure they are going to be awfully slow.

torgrot

---

### Post by smurphy_it on 2008-01-21
You don't need to download compiz at all, it is already installed and working.  At best, you would only have to download the compizconfig-settings-manager.  (type apt-get install compizconfig-settings-manager in a terminal window).  

Also, it may be your generic driver that is the problem.  Compiz should work without the 3D effects enabled, but to see in a terminal type ***glxinfo | grep rendering***

That should tell you if direct 3D rendering is enabled or not with the driver you are using.

If the restricted drivers aren't working for you, you could try [envy]("http://albertomilone.com/nvidia_scripts1.html").

[COLOR="DarkRed"]*Ps.  To get to a terminal click on Applications, Accessories, terminal.*[/COLOR]

---

### Post by _anant on 2008-01-21
i don't want great 3d effects >Good lord,can't i even get the NORMAL effects?and i have already tried envy.
that gbdinfo | grep... command gave the following message:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
what does this mean?

---

### Post by _anant on 2008-01-21
someone plz help

---

### Post by _anant on 2008-01-22
do i need display effects for watching videos\flash content?i can't  open the websit "www.springfest.in" correctly though i have a gnash flash player installed on my browser

---

### Post by _anant on 2008-01-22
i have a gnash player yet i am not able to open the site "www.springfest.in" correctly.Is this because the normal display effects are not enabled?

---

### Post by rosegarden78 on 2008-01-23
Try this:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
worked for me on Xubuntu with Intel 915 graphics.

---

### Post by rosegarden78 on 2008-01-23
This gave me Mac dock and Vista eye candy (compiz)
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
Awesome!

---

### Post by rakusson on 2008-02-26
hi, I have ATI Radeon RV250 FireGL9000 driver but I cannot enable display effect (even the simple one). 

I tried to check direct rendering support and vendort through
```

ra@everest:~/Desktop$ glxinfo | grep "direct rendering"
direct rendering: Yes
ra@everest:~/Desktop$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.


```

I have found that my card also supports 3D [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

What should I do to use/enable  display effect?

---

