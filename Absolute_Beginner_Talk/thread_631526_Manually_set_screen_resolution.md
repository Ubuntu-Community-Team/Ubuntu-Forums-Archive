---
title: "Manually set screen resolution"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by onlyproductions on 2007-12-04
how do i manually set a computers screen resolution, because whenever i boot ubuntu the screen comes up with the error resulotion must be set to something x something. and then the monitor powers off

---

### Post by jken146 on 2007-12-04
First, try System > Preferences > Screen Resolution.  If the one you want isn't in there and you know that your graphics card and monitor are capable of it, then see this tread: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)


edit: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by onlyproductions on 2007-12-04
i would but b4 the graphical interface starts the monitor turns off and is there any easier way which involves no terminal stuff

---

### Post by bodhi.zazen on 2007-12-04
what videocard are you using ?

Does the screen work from a live CD ?

---

### Post by SpacePilot on 2007-12-04
You edit it in your xorg.conf file.

in /etc/X11/xorg.conf you will find resolutions for different color depths. So you can just change the ones that are there to something you want. 

Say eg mine say:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [Quadro NVS 135M]"
    Monitor        "Standard skjerm"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1440x1050"
    EndSubSection
EndSection


If I wanted eg 1920x1200 resolution I could just change it there..


If you are running a nvidia card the nvidia-settings configurations utility is pretty good.

To run it you type gksudo nvidia-settings


Sorry but if you have no valid screens running you will have to be using the terminal.

---

