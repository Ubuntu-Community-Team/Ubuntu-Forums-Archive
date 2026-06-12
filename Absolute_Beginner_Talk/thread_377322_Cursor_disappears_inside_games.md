---
title: "Cursor disappears inside games"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by terrysalmi on 2007-03-05
I'm running Ubuntu Edgy on a Gateway MX3215 laptop and I've noticed inside some games, notably KBounce and Frozen Bubble, that as soon as I move my mouse cursor inside the playing area, the mouse cursor will disappear, effectively making it impossible to play a game like KBounce/Jezzball.  The only thing I can think of is that there was an error with my Java installation, which I installed using the apt-get method described at [http://wiki.serios.net/wiki/Ubunu_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Ubunu_Java_JRE/JDK_installation)

Here's part of my xconf file if it helps at all.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "no"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```

Thanks in advance for any help!

---

### Post by akiro.yamamoto on 2007-03-06
This is not an error.....
You use the direction keys... not the mouse....

---

### Post by steven8 on 2007-03-06
I don't know about KBounce or JezzBall, but Frozen Bubble is just meant to be run by the keyboard.

---

### Post by terrysalmi on 2007-03-06
> **akiro.yamamoto said:**
> This is not an error.....
You use the direction keys... not the mouse....

Maybe in Frozen Bubble, but definitely not in KBounce.  This game relies on the mouse.

---

### Post by akiro.yamamoto on 2007-03-06
I stand corrected.....
KBounce indeed relies on mouse actions to operate...

This is what my mouse config looks like```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

---

### Post by steven8 on 2007-03-06
The KBounce handbook specifically states you click on the playing surface.  Hmm.

Here is a link to the handbook:

[http://rds.yahoo.com/_ylt=A0geu56I.uxFqoAA5ChXNyoA;_ylu=X3oDMTE2Z2N1aWs1BGNvbG8DZQRsA1dTMQRwb3MDMwRzZWMDc3IEdnRpZANGODc1Xzgx/SIG=12e28hkdo/EXP=1173244936/**http%3a//docs.kde.org/stable/en/kdegames/kbounce/kbounce.pdf]("http://rds.yahoo.com/_ylt=A0geu56I.uxFqoAA5ChXNyoA;_ylu=X3oDMTE2Z2N1aWs1BGNvbG8DZQRsA1dTMQRwb3MDMwRzZWMDc3IEdnRpZANGODc1Xzgx/SIG=12e28hkdo/EXP=1173244936/**http%3a//docs.kde.org/stable/en/kdegames/kbounce/kbounce.pdf")

---

### Post by terrysalmi on 2007-03-06
> **steven8 said:**
> The KBounce handbook specifically states you click on the playing surface.  Hmm.

Here is a link to the handbook:

[http://rds.yahoo.com/_ylt=A0geu56I.uxFqoAA5ChXNyoA;_ylu=X3oDMTE2Z2N1aWs1BGNvbG8DZQRsA1dTMQRwb3MDMwRzZWMDc3IEdnRpZANGODc1Xzgx/SIG=12e28hkdo/EXP=1173244936/**http%3a//docs.kde.org/stable/en/kdegames/kbounce/kbounce.pdf]("http://rds.yahoo.com/_ylt=A0geu56I.uxFqoAA5ChXNyoA;_ylu=X3oDMTE2Z2N1aWs1BGNvbG8DZQRsA1dTMQRwb3MDMwRzZWMDc3IEdnRpZANGODc1Xzgx/SIG=12e28hkdo/EXP=1173244936/**http%3a//docs.kde.org/stable/en/kdegames/kbounce/kbounce.pdf")

Right.  It states 

> When the mouse is on the field, the cursor is shown as a pair of arrows pointing
in opposite directions, either horizontally or vertically. 

Meaning there should be some type of cursor on the playing screen.  Instead, as soon as I move my mouse over the active playing surface, I get nothing at all.

---

### Post by sohaibma on 2007-03-06
I am facing similar problem, however my problem is not limited to games.
It also happens when i try to use tome softwares like inkscape, amarok, etc.

---

### Post by steven8 on 2007-03-06
May be an issue of running  a KDE game in a Gnome environment?

---

### Post by sohaibma on 2007-03-06
i'm sure its not because i'm running a kde app in gnome, because the mouse also disappears in other apps like adobe reader
its due to something else

---

### Post by terrysalmi on 2007-03-06
Exactly.  I also had the problem on the configuration page of Wine, but have since uninstalled it so I didn't put it in the list, and just KBounce, etc. which I currently have up and not working properly.

Sure is a bummer, too.  :(

---

### Post by terrysalmi on 2007-03-06
Shoot, this is just getting worse now.  It also happens inside Firefox when I try to add a new item to the toolbar.  As soon as the cursor enters the part of the screen where the buttons are, it disappears.  Using guesswork I can still click in the right places, but I know something is up.

---

### Post by terrysalmi on 2007-03-06
I fixed the problem!!!  

Add this line to xorg.conf....

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "via"
        BusID           "PCI:1:0:0"
        **Option          "HWCursor"              "Off"**

```

---

### Post by steven8 on 2007-03-06
> **terrysalmi said:**
> I fixed the problem!!!  

Add this line to xorg.conf....

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "via"
        BusID           "PCI:1:0:0"
        **Option          "HWCursor"              "Off"**

```

That's great.  How did you think to put that in there?

---

### Post by terrysalmi on 2007-03-06
> **steven8 said:**
> That's great.  How did you think to put that in there?

I originally saw a blurb on the OpenChrome video driver install page about putting a SWCursor note in xorg.conf, as well as other sites mentioning HWConf also being the same but opposite.  I tried putting this in the mouse section but to no result.

Finally one of my random searches using every keyword possible paid off, and I came across this post, which gave me the idea to put it in the Video section....

[http://www.ubuntuforums.org/showthread.php?t=236714](http://www.ubuntuforums.org/showthread.php?t=236714)

---

### Post by steven8 on 2007-03-06
> **terrysalmi said:**
> I originally saw a blurb on the OpenChrome video driver install page about putting a SWCursor note in xorg.conf, as well as other sites mentioning HWConf also being the same but opposite.  I tried putting this in the mouse section but to no result.

Finally one of my random searches using every keyword possible paid off, and I came across this post, which gave me the idea to put it in the Video section....

[http://www.ubuntuforums.org/showthread.php?t=236714](http://www.ubuntuforums.org/showthread.php?t=236714)


Good work!!

---

### Post by sohaibma on 2007-03-12
please  help me!!!!!

---

