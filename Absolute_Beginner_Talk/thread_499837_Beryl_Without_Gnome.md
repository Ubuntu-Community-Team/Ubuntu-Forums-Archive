---
title: "Beryl Without Gnome"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Mrhankymk on 2007-07-13
Hello,

I recently had to install Wicd to connect to my hidden network. This disabled Gnome (I'm pretty sure). The problem is that I really wanted to install Beryl just because it looks cool and has that nice box function and to brag about it to friends to get them on Ubuntu as well and I'm pretty sure Beryl requires Gnome. I downloaded and installed Beryl in my Synaptic Application Manager and then enabled it as my Window manager. After enabling it the top of the window where you minimize, maximize, and close the window as well as view the application title and icon disappears and I am no longer able to switch or activate new windows.
Basically what do I need to do to get Beryl working and still keep Wicd?

Thanks for all the help..

Matt

---

### Post by mikewhatever on 2007-07-13
What do you mean by 'disabled Gnome'? Gnome is a desktop environment that includes a lot of thins (programs, themes etc). 
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)
The problem with windows' borders is probable unrelated to wicd, but should be related to Beryl. What video driver do you use? Can you post the output of the following command
> cat /etc/X11/xorg.conf

---

### Post by Mrhankymk on 2007-07-13
Thanks for the reply. I got a huge return but here's what I think you were looking for -
> Section "Device"
        Identifier      "Intel Corporation 82946GZ/GL Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

---

### Post by mikewhatever on 2007-07-13
Well, the output is not that big, about 3 pages if you maximize the terminal window. Can you also check the following section:
> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    [COLOR="Red"]DefaultDepth    24[/COLOR]
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
    [COLOR="Red"]SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection[/COLOR]
EndSection


What's the default depth you have? Not sure it will work with Intel Integrated, but if the default depth is say 16, edit it to 24 making sure there is a corresponding section below.

---

### Post by Circus-Killer on 2007-07-13
> **Mrhankymk said:**
> Hello,

I recently had to install Wicd to connect to my hidden network. This disabled Gnome (I'm pretty sure). The problem is that I really wanted to install Beryl just because it looks cool and has that nice box function and to brag about it to friends to get them on Ubuntu as well and I'm pretty sure Beryl requires Gnome. I downloaded and installed Beryl in my Synaptic Application Manager and then enabled it as my Window manager. After enabling it the top of the window where you minimize, maximize, and close the window as well as view the application title and icon disappears and I am no longer able to switch or activate new windows.
Basically what do I need to do to get Beryl working and still keep Wicd?

Thanks for all the help..

Matt

just outta interest, did you install emerald and emerald-themes?

---

### Post by Mrhankymk on 2007-07-13
No themes yet. I'm about to though. You recommend emerald?
Result -
> 
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82946GZ/GL Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


---

### Post by mcduck on 2007-07-13
Emerald is the part of Beryl that draws the window decorations. So if you haven't got Emerald installed it's no surprise yur window decorations aren't working ;)

---

### Post by Mrhankymk on 2007-07-13
And where would I install this? I can't seem to find it.

---

### Post by overdrank on 2007-07-13
> **Mrhankymk said:**
> And where would I install this? I can't seem to find it.

Hi you can use this command in the terminal
```
sudo apt-get install emerald-themes
```
GOOD Luck!:guitar:

---

### Post by Xoanan on 2007-07-13
Let me know if it works;  I have an i810 card as well(of course, I might need to buy more RAM though, only 128 MB)

---

