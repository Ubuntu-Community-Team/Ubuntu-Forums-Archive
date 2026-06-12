---
title: "Some random quick questions"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-21
Now that I seem to be stably on the internet, I have a couple questions that will hopefully be enough for me to continue to sail and figure out most of the rest on my own:
[INDENT]1. I have this feature disabled in Windows, but the laptop's touchpad is driving me nuts. I don't want it to interpret a tap as a left-click. Even the gentlest tap >.<
2. I have attempted to install a program or two via the Add/Remove Applications menu. But now I do not know where they have gone, or how to execute them? If it helps the one I am most curious about is "Celestia" (in the "other" category)
3. When I ran Firefox earlier it stopped recognizing files/web pages with the .phtml extension, however when I opened new Firefox window via the terminal everything worked fine (same pages, no less!) Should I be downloading a plugin or something, or was this just a "hiccup"?
4. Does anyone know any good "intro to linux/ubuntu" tutorials? I googled for some but the best I found was [this one]("http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/"). I am looking for something that will give me any aid learning the new terminal commands (so I guess they aren't new... but I'm still thinking in "terminal vs. cmd (Windows)" mode), or installing/running progams (I was looking to install XGL, however after seeing how complex that is I started to look at Beryl, but I don't even know).[/INDENT]
Any help is greatly appreciated, as always :D

---

### Post by 23meg on 2006-11-21
>     1. I have this feature disabled in Windows, but the laptop's touchpad is driving me nuts. I don't want it to interpret a tap as a left-click. Even the gentlest tap >.<[http://ubuntuforums.org/showpost.php?p=1651101&postcount=5](http://ubuntuforums.org/showpost.php?p=1651101&postcount=5)
> 2. I have attempted to install a program or two via the Add/Remove Applications menu. But now I do not know where they have gone, or how to execute them? If it helps the one I am most curious about is "Celestia" (in the "other" category)Look at your Applications menu, if they're not there, try restarting the GNOME panel with ```
killall gnome-panel
```You can also hit Alt+F2 and type the name of the program to run it.
> 4. Does anyone know any good "intro to linux/ubuntu" tutorials?
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://linuxcommand.org](http://linuxcommand.org)

---

### Post by CupofDice on 2006-11-21
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) They also have a breezy/eft page somewhere on that site.
The psychocats, and monkey blog 23meg recommended are really good too.
Also check out the howto section here.

---

### Post by seijuro on 2006-11-21
For the tap fuction open a terminal and edit your xorg.conf

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"    ##(find this section)
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on" ##(Add this line)
EndSection

```
then in the console type
```

synclient RTCornerButton=0 RBCornerButton=0 TapButton1=0 TapButton2=0 TapButton3=0

```
you can add the synclient command to a script and have it run when X starts  if you don't want to manually do it each time

---

### Post by nonpareilpearl on 2006-11-21
**23meg**: For #1- I have no idea where that file is, and I tried searching for the filename and extension but it doesn't come up.
For #2- THANK YOU!
and #4- I'll probably be looking through this over break :)

---

### Post by nonpareilpearl on 2006-11-21
For #1: Disregard that I found it (I love Google sometimes :))

---

### Post by 23meg on 2006-11-21
You can open it with this command ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by nonpareilpearl on 2006-11-21
I tried both entering the line mentioned in the linked thread above, and the "synclient" instructions (via **seijuro**), but it's still tapping :(

---

### Post by 23meg on 2006-11-21
You'll need to restart X. Make sure you have no unsaved work and hit Ctrl + Alt + Backspace if you haven't.

---

### Post by nonpareilpearl on 2006-11-21
I rebooted after trying both, and the MaxTapTime worked, thank you :D

---

