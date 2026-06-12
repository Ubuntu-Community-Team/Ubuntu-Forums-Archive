---
title: "compiz desktop effects problem"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by nraney on 2007-09-24
I'm new.  I hope this is an easy fix.
whenever I go into the system drop down and select desktop effects or GL Desktop (compiz) it changes all the windows to be unmovable and the title bar loses its minimize/maximize/close function.  So I have to revert back to normal settings.

I am using Nvidia X server on a HP v3000 Laptop.

Any first impressions or simple settings I should change to make this work?

Thanks,
nraney

---

### Post by RomeReactor on 2007-09-24
Hi. After enabling Desktop Effects, try restarting the X server by pressing CTRL+ALT+BACKSPACE; now log in and see if you still have that problem.

That's happened to me sometimes; another way to deal with an unmovable window is to press ALT and then move it. That usually solves that issue for me. As for being unable to minimize/maximize, closing the application/window and opening it again fixes that.

I know these are just workarounds; I don't know what causes the problems, or the solution.

---

### Post by Fitzy_oz on 2007-09-24
> **RomeReactor said:**
> Hi. After enabling Desktop Effects, try restarting the X server by pressing CTRL+ALT+BACKSPACE; now log in and see if you still have that problem.

That's happened to me sometimes; another way to deal with an unmovable window is to press ALT and then move it. That usually solves that issue for me. As for being unable to minimize/maximize, closing the application/window and opening it again fixes that.

I know these are just workarounds; I don't know what causes the problems, or the solution.

Does the title bar(s) and window border(s) disappear?  If so this is a problem with the xorg.conf file missing an entry.  Have you used the nvidia-settings wizard to change your resolution at all and saved the config file?

---

### Post by nraney on 2007-09-24
yes the window boarders disappear - i cant seem to figure out how to get to nvidia settings wizard.  how do i do it?

---

### Post by phizikal on 2007-09-24
ALT-F2  and put in "nvidia-settings" or type it in the shell.

---

### Post by overdrank on 2007-09-24
> **phizikal said:**
> ALT-F2  and put in   
]nvidia-settings or type it in the shell.

I would suggest the terminal
```
sudo nvidia-settings
```
this will allow you to save the settings

---

### Post by RomeReactor on 2007-09-24
> **nraney said:**
> yes the window boarders disappear
That's a different problem then, as **Fitzy_oz** said. Try calling nvidia-settings as **phizikal** says, but do so using sudo, so the changes you make can be saved:
```
gksudo nvidia-settings
```

EDIT: beaten by overdrank...

---

### Post by overdrank on 2007-09-24
> **RomeReactor said:**
> That's a different problem then, as **Fitzy_oz** said. Try calling nvidia-settings as **phizikal** says, but do so using sudo, so the changes you make can be saved:
```
gksudo nvidia-settings
```

EDIT: beaten by overdrank...

Or as RomeReactor suggest will work also!

---

### Post by nraney on 2007-09-25
oh i didnt realize that was the dialog in question.  yes i could get to the general nvidia settings box the whole time.. but a wizard?  I dont know what my screen settings should be.

---

### Post by Fitzy_oz on 2007-09-25
> **nraney said:**
> oh i didnt realize that was the dialog in question.  yes i could get to the general nvidia settings box the whole time.. but a wizard?  I dont know what my screen settings should be.

It's not really a wizard per say, did you select a resolution in there and then save it to your xorg.conf file whe  you were done.  ANyway, here's the fix:
drop a terminal and type the following - 
**sudo nvidia-xconfig --add-argb-glx-visuals**

hit ctrl+alt+backspace to restart x and log back in, you should be right after that ;)

---

### Post by RomeReactor on 2007-09-25
Well, according to **Fitzy_oz**, your xorg.conf file is missing an entry; try posting it:
```
cat /etc/X11/xorg.conf
```
Perhaps you're missing entries in **"Section Device**.

EDIT: now beaten by Fitzy_oz...

---

### Post by nraney on 2007-09-25
well i did get something back in terminal:
nraney@nraney-laptop:~$ sudo nvidia-xconfig --add-argb-glx-visuals

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen1".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

after that, i did a ctrl+alt+backspace and logged back in.. the first thing i tried was desktop effects.. i  tried gl desktop also, but no go still no title bar at all..

is it bad that i have no idea what is happening behind what you are telling me to do?

---

### Post by Fitzy_oz on 2007-09-25
> **nraney said:**
> well i did get something back in terminal:
nraney@nraney-laptop:~$ sudo nvidia-xconfig --add-argb-glx-visuals

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen1".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

after that, i did a ctrl+alt+backspace and logged back in.. the first thing i tried was desktop effects.. i  tried gl desktop also, but no go still no title bar at all..

is it bad that i have no idea what is happening behind what you are telling me to do?

That should have fixed it :-?
Can you post your xorg.conf file here for us and we'll take a look at it, edit it if necessary and then you can copy it down and save it :).

---

### Post by RomeReactor on 2007-09-25
You have every right to ask what you're being told to do to your system; essentially, that command adds an option to a file called **xorg.conf** (which manages your display's settings). To view the xorg.conf file in full, try this command:
```
gedit /etc/X11/xorg.conf
```
That will open the file (xorg.conf) located in **/etc/X11** in the text editor (gedit). Scroll down to **"Section" Device** to see the options it has.

EDIT: late again... Also: do you have two monitors? the output shows two screens...

---

### Post by nraney on 2007-09-25
Ok I believe I understood all that. 
when I open the xorg.conf file in gedit it appears to be completely blank.

The guy that set me up with ubuntu (I was on a lonely path to no-where as a windows user previously) said he did some things to the nvidia settings to enable me to use my s-video output (which i havnt even tested yet).  This may be why it reports two screens.

I tried the cat /etc/X11/xorg.conf  and it reported:
nraney@nraney-laptop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:38:28 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "metamodes" "DFP: 1280x800 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    16
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by RomeReactor on 2007-09-25
Now *that* is odd; are you certain you entered the command *exactly* as it appears in my previous post? maybe there's a typo. Close gedit and try copy/pasting the command into your terminal.

---

### Post by Fitzy_oz on 2007-09-25
> **nraney said:**
> Ok I believe I understood all that. 
when I open the xorg.conf file in gedit it appears to be completely blank.

The guy that set me up with ubuntu (I was on a lonely path to no-where as a windows user previously) said he did some things to the nvidia settings to enable me to use my s-video output (which i havnt even tested yet).  This may be why it reports two screens.

hmm, thats not good... is there a chance you typed the path wrong, it's case sensitive.  Try copy this exactly and pasting it into the terminal.  

gksudo gedit /etc/X11/xorg.conf then copy whats there and paste it here :)

Anywaye svideo output would almost certainly be what the additional screen is for and if he;s changed your config using the nvidia-settings utlilty, it doesn't add the line i specified earlier and effectively breaks compiz...  Keep plugging we'll get you there ;)

---

### Post by nraney on 2007-09-25
sorry i edited my last post i should have just replied.  check my last post again, i reported what it gave me from cat /etc/X11/xorg.conf

---

### Post by Fitzy_oz on 2007-09-25
> **nraney said:**
> Ok I believe I understood all that. 
when I open the xorg.conf file in gedit it appears to be completely blank.

The guy that set me up with ubuntu (I was on a lonely path to no-where as a windows user previously) said he did some things to the nvidia settings to enable me to use my s-video output (which i havnt even tested yet).  This may be why it reports two screens.

I tried the cat /etc/X11/xorg.conf  and it reported:
nraney@nraney-laptop:~$ cat /etc/X11/xorg.conf


Ok here we go - I found a couple of things - Added the line to the device section, and changed the default color depth to 24bit, this is what could be causing th issues as i don't think compiz likes 16 bit.
You can use the command we pointed out earlier in the terminal to edit the xorg.conf file (gksudo gedit /etc/X11/xorg.conf) and save a copy of that file as a backup and then delete everything in the file and paste this in it's palce... Save the file and cross your fingers :)

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:38:28 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    BusID          "PCI:0:5:0"
    Screen          1
   Option          "AddARGBVisuals"        "True"
   Option          "AddARGBGLXVisuals"     "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1280x800 +0+0"
    Option         "AddARGBGLXVisuals" "True"     
   SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    
EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by RomeReactor on 2007-09-25
If I'm not mistaken you should have these two options
```
Option          "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
```
in **"Section"  Device** instead of **"Section"  Screen**, just below the **BusID** entry.

EDIT: Oh, and as Fitzy_oz says, make sure you backup the xorg.conf file; if you back it up with gedit, remember to close it after you make the backup and then open it again using the same command. If you continue using the file after you make the backup in gedit, you'll be editing the **backup**, not the original which is what you want.

Another way to back up the file using the terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
That will make a backup called **xorg.conf.backup** in the same folder as the original; if for whatever reason you need to restore it, use:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by Fitzy_oz on 2007-09-25
> **RomeReactor said:**
> If I'm not mistaken you should have these two options
```
Option          "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
```
in **"Section"  Device** instead of **"Section"  Screen**, just below the **BusID** entry.

You are correct, there are two, mine does however work with just the one, I just ssh'd in and checked my config (im doing this from work on a windows box:()  I'll change the previous post :)

---

### Post by nraney on 2007-09-25
Thank you, Good info Rome, im slowly learning my terminal commands.... but I had already fixed it with Fitzy_Oz's!!! Hell yeah!  Y'all are the best gurus I've ever encountered in my life.  I'm very grateful. 

its working beautifully.

on a side note do you know of anything in linux that will mimic the Mac Powerbook were it has two views of the desktop, one where it shows all the windows at about 20% and it lets you quickly choose which one you want and brings it up to 100%?

Thanks again guys.
nraney

---

### Post by Fitzy_oz on 2007-09-25
> **nraney said:**
> Thank you, Good info Rome, im slowly learning my terminal commands.... but I had already fixed it with Fitzy_Oz's!!! Hell yeah!  Y'all are the best gurus I've ever encountered in my life.  I'm very grateful. 

its working beautifully.

on a side note do you know of anything in linux that will mimic the Mac Powerbook were it has two views of the desktop, one where it shows all the windows at about 20% and it lets you quickly choose which one you want and brings it up to 100%?

Thanks again guys.
nraney

You are most welcome :)

Beryl has something similar to that as does compiz fusion - Have a search for the compiz plugins and see what you come up with :)  I'm sure there's one there...

---

### Post by nraney on 2007-09-25
actually I figured it out.  if you press control alt and up it does exactly what I was asking.. super awsome.  I will be looking for this other info on compiz fusion thanks for the head start.

---

### Post by phelixnyc on 2007-09-25
next time use this tutorial [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
I believe it has a walk around for your problem.

---

### Post by nraney on 2007-09-25
two more quick questions.
how do I check which version of compiz I have?
Why did my gnome compiz preferences/effects/water work right after we got the desktop effects accomplished but then suddenly stop working (after a reboot)? boo! This isnt a big deal guys, if you have to try.. dont even worry about it.

---

### Post by RomeReactor on 2007-09-25
To check which version of Compiz you have:
```
compiz.real --version
```
As for the effects not sticking between reboots, you mean they're disabled, or certain effects don't work?

---

### Post by nraney on 2007-09-25
thanks. I have compiz 0.3.6.

I think the newest version stable for fiesty is 0.4.0 so im gonna look around the forums for how to update.  maybe a good idea.

the effect water doesnt work, and it bugs out when I try get it to use multiple desktops.  it manages switching multiple viewports well enough.

---

