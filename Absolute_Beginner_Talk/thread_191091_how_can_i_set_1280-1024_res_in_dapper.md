---
title: "how can i set 1280-1024 res in dapper"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-06-07
i just did a clean install of the official 6.06 release and have a 17" lcd monitor. i installed the latest nvidia driver and have enabled nvidia settings but in system>preferences>screen res, the highest res is 1024-768. also i can't see how to change the resolution in nvidia settings. can anyone help me? thanks

---

### Post by jvictor on 2006-06-07
You need to know your monitors h/v refresh rates for it , the monitors manual or a search on the net will give u the exact h/v rates.

sudo gedit /etc/X11/xorg.conf

Find this section

Section "Monitor"
..........
...........
EndSection



and insert

        HorizSync XX - XX
        VertRefresh XXX - XXX

to make it look like

Section "Monitor"
        Identifier      ......
        Option          ......
        HorizSync XX - XX
        VertRefresh XX - XX
EndSection

REPLACE X with actual rates

30 - 70
50 - 120 is my monitors h/v refresh (17" CRT Samsung Syncmaster Flat)

 SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection


save , logout,  ctl+alt+backpace

EDIT :: NOT sure abt whether u need refresh rates, for a LCD monitor

---

### Post by stephen_lau on 2006-06-07
Do:
```
sudo /etc/X11/xorg.conf
```
and goto the "Screen" section, and add in the resolution "1280x1024" in Modes. This is my xorg.conf to show you what you should have:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "BenQ FP71E"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection

```

Save the file, CTRL + ALT + BACKSPACE to restart X (this will log you out). Then you will be able to see the 1280 x 1024 resolution under System --> Preference --> Screen Resolution

edit: refresh rate is not needed, since you are using LCD screen

---

### Post by e1ektrob0y on 2006-06-07
[QUOTE=stephen_lau]Do:
```
sudo /etc/X11/xorg.conf
```
and goto the "Screen" section, and add in the resolution "1280x1024" in Modes. This is my xorg.conf to show you what you should have:

[/QUOTE]
```
sudo /etc/X11/xorg.conf

sudo: /etc/X11/xorg.conf: command not found
```
are you sure thats the right code?

---

### Post by stephen_lau on 2006-06-07
sorry, should be:

```
sudo gedit /etc/X11/xorg.conf
```

:oops:

---

### Post by xrchris on 2006-06-07
should be  ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by e1ektrob0y on 2006-06-07
no worries. actually this is what i have in that gedit file. seems my monitor has not been identified yet maybe? cause it says "generic monitor".
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by stephen_lau on 2006-06-07
That's alright, the name of the monitor doesn't really matter (I renamed mine :P) . Just add the 1280x1024 to each of the subsections, restart X, and it should work.

---

### Post by Kobalt on 2006-06-07
Hi, 

Or you could try to run : 
```
sudo dpkg-reconfigure xserver-xorg
```
and chose the resolutions you want as avaliable. 

Don't forget to restart X after your changes : CTRL+TAB+BACKSPACE

Cheers !

---

### Post by e1ektrob0y on 2006-06-07
sweet it worked, thanks all :)

---

