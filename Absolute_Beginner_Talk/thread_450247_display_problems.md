---
title: "display problems"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by shonuf on 2007-05-21
i have installed Feisty Fawn on my desktop fine with no problems so i know this is not a instaliation problem

but when i installed it on my laptop it seems like everything is working fine and correct but it seems that the screen is split into 2 and they are overlapping

my laptop is a Dell Latitude C600 with an ATI Rage Mobility M3 AGP 2x (according to Ubuntu's Hardware Manager)

like if i were to drag a window from the far left and drag it to the far right it wouldnt move like

Left  ---> Center ---> Right

it moves

Left ---> Right ----> Center


the left side is completely fine and everything runs smoothly its just the display is messed up and i  have no idea what to do

i tried taking a screenshot of it but in the screenshot the desktop looks fine

---

### Post by apienk01 on 2007-05-21
Ati Rage 128 is an old card, and on some laptops Linux has problems using it. One solution is changing the screen depth from 32-bit to 16-bit in xorg.conf. And don't forget to set the right resolution (fitting your LCD) in the file.

Hope it helps.

---

### Post by Outrunner on 2007-05-21
Hey there, just thought I'd clarify on what Apienk01 said.

First you go to applications > accessories > terminal and type

```
gksudo gedit /etc/X11/xorg.conf
``` (notice the capital X in X11, it's very important).

now there will be a sections that looks somewhat like this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

To change the depth just modifi this part:

"    DefaultDepth    24    "

to look like

"    DefaultDepth    16    "

EDIT: And of course, how could I forget?! After this close all your applications and do a CTRL+ALT+BACKSPACE to restart the xserver and log back in.

---

### Post by shonuf on 2007-05-21
you guys are gods

i was looking all night for a solution to that problem and you fixed it in a couple of sentences



thank you very very much

---

### Post by wagnercg80 on 2007-08-20
This worked for my Dell Latitude C600 with an ATI Mobility M3 AGP 2X and Feisty Fawn.  I used the Alternative install CD.

My problem was similar in that the screen seemed segmented in three or so vertical segments that "sort of" went together but the segments were out of order.  Now I am checking another discussion thread.  My screen resolution choices are 800x600 and 640x480.  I saw a thread:
[http://ubuntuforums.org/showthread.php?t=411489&highlight=ati+mobility+dell+c600](http://ubuntuforums.org/showthread.php?t=411489&highlight=ati+mobility+dell+c600)

This community rocks.

---

