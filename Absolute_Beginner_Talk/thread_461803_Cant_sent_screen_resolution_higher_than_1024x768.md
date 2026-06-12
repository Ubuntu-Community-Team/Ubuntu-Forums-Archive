---
title: "Cant sent screen resolution higher than 1024x768"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Quan_Chi on 2007-06-02
Ive tried two ways of making my screen res higher.
1.System>Preferences>Screen Resolution
But when I get there it wont let me set it higher than 1024x768

2.In the terminal I typed "aticonfig --resolution=1280x1024" like it says to do in the aticonfig.
But I get this

quanchi@quanchi-desktop:~$ aticonfig --resolution=1280x1024
Segmentation fault (core dumped)


This large resolution is killing me :/

Some one please help.

---

### Post by Ek0nomik on 2007-06-02
Have you tried to run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use the space bar to select options and resolutions.

---

### Post by Quan_Chi on 2007-06-02
I get this

quanchi@quanchi-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070602000807

---

### Post by Ek0nomik on 2007-06-02
Run it again.

---

### Post by Quan_Chi on 2007-06-02
I recive the same message :/

---

### Post by alienexplorers on 2007-06-02
Disreguard the message.  It is only making a backup copy of xorg.conf.

---

### Post by Quan_Chi on 2007-06-02
ok so how do I change my screen resolution

---

### Post by alienexplorers on 2007-06-02
When you get to the page about resolutions scroll up or down till you find the resokution you are looking for and use your space key to select it,  Finish up and save and reboot.

---

### Post by Nythain on 2007-06-02
you could just edit your xorg.conf file and add the res you want to run at

gksudo gedit /etc/X11/xorg.conf

find section that looks like this
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```and add the resolutions you want to be able to select... btw it will default run at the first res in the list as long as its a supported res

---

### Post by freebird54 on 2007-06-02
From what I can see this is often the result of an undetected monitor.  One easy way to check is to look at the configuration file.

Open an Applications->Accessories->Terminal window and enter:

```
less < /etc/X11/xorg.conf
```

space bar will advance a page, 'q' to quit.  You are looking for a section like this:

```
Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30 - 50
        VertRefresh  42 - 60
        Option      "DPMS"
EndSection
```

If it has similar HorizSync and VertRefresh numbers, and they don't match your monitor's capabilities, it will refuse to go hi-res (for fear of burning the monitor).  Here is my monitor entry (a CRT from Samsung) and its number allow up 1600X1200 if I want to go there.  (JUST AN EXAMPLE)

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection
```


You can see the diference!  If your monitor is not correctly detected, you can entger the correct numbers from your monitor manual, or from the Web if you can't find the manual.  *OR* you can re-run the dpkg-reconfigure thing again, and make sure you choose medium or advanced monitor settings.  Try this link:  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)   for step by step walkthrough of the process....

Good luck - you *WILL* get it :)

---

