---
title: "white sceen &amp; general question"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-04
i have everything running pretty good now, all on one partition and all the hardware seems to have been installed correctly however when i go to turn windows effects on the whole screen turns white during the preview mode... i assume this is a vid driver problem?
ati radeon 850 Platinum Edition is what i have, and in my hardware profile it seems that the driver was installed correctly for this as well

2nd, when downloading programs, not everything is download, double click and auto install.. is there a 3rd party program to streamline such things?

---

### Post by torgrot on 2007-05-04
The ATI restricted driveer doesn't suppport the composite extension.  So desktop effects are not supported withe the ATI restricted driver.  Disable the ATI restricted driver and you can see the Desktop Effects.  I am assuming you are running Fiesty.

torgrot

---

### Post by silent1643 on 2007-05-04
ah i see, so there is no perm fix for this situation.. if i disable the video card driver then my graphics want be setup right for other programs?

---

### Post by silent1643 on 2007-05-05
anybody? how do i Disable the ATI restricted driver? or fix this problem so i can run compiz?

---

### Post by freebird54 on 2007-05-05
First thing - is that 850 Radeon an X850 ?  If it is, there is an outstanding issue on the X series cards that keeps things from being simple.  It does NOT prevent a fix though.  I am assuming that you have the fglrx driver installed.  To get the desktop effects working, you'll have to use XGL as your environment, rather than the default AIGLX environment for handling 3d effects.

Take a look for the feisty equivalent of this link:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
or you can even try it as is (it worked for me).  If you feel it is too much, then wait a while - a fix is being worked on, but I'm not sure how long it will take :)

---

### Post by silent1643 on 2007-05-07
> **freebird54 said:**
> First thing - is that 850 Radeon an X850 ?  If it is, there is an outstanding issue on the X series cards that keeps things from being simple.  It does NOT prevent a fix though.  I am assuming that you have the fglrx driver installed.  To get the desktop effects working, you'll have to use XGL as your environment, rather than the default AIGLX environment for handling 3d effects.

Take a look for the feisty equivalent of this link:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
or you can even try it as is (it worked for me).  If you feel it is too much, then wait a while - a fix is being worked on, but I'm not sure how long it will take :)

its the xt pe (platinum edition) card  - i do have a navida 7300 le card that i could use instead.. do you think this card would work better, and run well for beryl or compiz?

---

### Post by freebird54 on 2007-05-07
I am not familiar with the model designations on nVidia - but there sure are a lot of people who swear by them (rather than at them).  The biggest advantage that I can see for them is that the drivers provided by the manufacturer appear to work with AIGLX - so you don't need to jump through hoops or put up with XGL incompatibilities (in games for instance) that come with a working XGL Beryl setup..

So - if it's an easy switch - I'd have to consider it....

---

### Post by silent1643 on 2007-05-07
> **freebird54 said:**
> I am not familiar with the model designations on nVidia - but there sure are a lot of people who swear by them (rather than at them).  The biggest advantage that I can see for them is that the drivers provided by the manufacturer appear to work with AIGLX - so you don't need to jump through hoops or put up with XGL incompatibilities (in games for instance) that come with a working XGL Beryl setup..

So - if it's an easy switch - I'd have to consider it....

right-o, im not sure what is involved with replacing a graphics card in linux, but i can only assume its just a matter of replacing the cards, booting up, and installing the right drivers.. if thats the case, then its an easy switch :D

---

### Post by freebird54 on 2007-05-07
I would suggest that you either:

a) replace references to special drivers in /etc/X11/Xorg.conf with 'vesa' before starting the swap out (and removing any special edits as well - if you know of them)  OR

b) making the first boot to recovery console, and running:

```
sudo dpkg-reconfigure xserver-xorg
```

to set up the new card right away.  Your choice, of course - but it seems simpler to me to use 'b' - and either way prevents hangs while telling the system about your change.  Of course, there may be a 'plug'n'play' option I don't know about that'll catch all this for you... but I haven't heard of it yet)

---

### Post by silent1643 on 2007-05-07
thanks for your help :D

---

### Post by Derspankster on 2007-05-08
> **silent1643 said:**
> thanks for your help :D
To get out of the white screen. Boot into terminal or command line and run dpkg-reconfigure xserver-xorg.  Remove glx from Section Module by arrow keying down to it and pressing your spacebar. That will remove the check from glx. Finish the rest of the screens and restart your system. The white screen should be gone.

---

### Post by silent1643 on 2007-05-08
thanks so is this a fix for the desktop effects white screen, or merely a way of rebooting the machine and not having the white screen anymore?
ie will i be able to use desktop effects after i do this?

---

### Post by izizzle on 2007-05-09
I'm having this same problem. I have an Nvidia Riva TNT 2 on my test machine (running ubuntu on) and an NVIDIA Geforce FX 5500 on my main system. will desktop effects work with the 5500?

---

### Post by silent1643 on 2007-05-09
> **izizzle said:**
> I'm having this same problem. I have an Nvidia Riva TNT 2 on my test machine (running ubuntu on) and an NVIDIA Geforce FX 5500 on my main system. will desktop effects work with the 5500?

dunno, i have even downloaded and tried [envy..]("http://www.albertomilone.com/nvidia_scripts1.html") might work for you but it made my top menu's (close, minimize, resize) disapear until i uninstalled

---

