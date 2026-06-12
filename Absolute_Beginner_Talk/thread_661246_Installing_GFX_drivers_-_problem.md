---
title: "Installing GFX drivers - problem?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-07
I have this video card, a PNY 7600GS, it'sa  512MB AGP card.

There's a few problems with it:  One, I need drivers, it's got the OEM ubuntu drivers but they're not doing jack, I need the manufacturer drivers:

[http://www2.pny.com/7600-GS-512MB-AGP--P1897C14.aspx](http://www2.pny.com/7600-GS-512MB-AGP--P1897C14.aspx)

I can't find jack **** worth of drivers for it - on their site or any other.

The regular ubuntu drivers are enough to make GLX gears and the compiz cube work well, but even full screen youtube vids completely fail.

Anybody know where I can find these things?

PS:  I really have no idea about installing drivers on a UNIX based system - and this forum gets a lot more hits than the multimedia forum...

---

### Post by Syndacate on 2008-01-07
*bump

Anybody?

---

### Post by RomeReactor on 2008-01-07
Hi. Did you enable the drivers in 'System->Administration->Restricted Drivers Manager'? If so, and you still have problems, run this from the terminal to see which version of the drivers was installed:
```
aptitude search nvidia-glx
```
and post the output. If the installed drivers are **nvidia-glx**, you may want to switch to **nvidia-glx-new**.

---

### Post by TechRavingMad on 2008-01-07
You could also go to nvidia's site if for some reason the restricted driver doesn't work:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

TRM

---

### Post by Syndacate on 2008-01-08
> **RomeReactor said:**
> Hi. Did you enable the drivers in 'System->Administration->Restricted Drivers Manager'? If so, and you still have problems, run this from the terminal to see which version of the drivers was installed:
```
aptitude search nvidia-glx
```
and post the output. If the installed drivers are **nvidia-glx**, you may want to switch to **nvidia-glx-new**.

I'm using the restricted driver - and I'm using something I found called "Envy" - but either way, it can't even view a youtube video (and that's not high quality) on full screen or it's choppy as hell.

Here's what **aptitude search nvidia-glx** revealed:
```

p   nvidia-glx                                                   - NVIDIA binary XFree86 4.x/X.Org driver
p   nvidia-glx-dev                                               - NVIDIA binary XFree86 4.x/X.Org driver development files
p   nvidia-glx-legacy                                            - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
p   nvidia-glx-legacy-dev                                        - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
i   nvidia-glx-new                                               - NVIDIA binary XFree86 4.x/X.Org 'new' driver
i   nvidia-glx-new-dev                                           - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files

```

As you can see something should work by now, not sure what the "i" and "p" mean but something is off.

I'll look on nvidia's site, though I think the ones I have installed are enough, I don't get what it's doing this, youtube at full screen shouldn't be that graphically intensive...

---

### Post by Syndacate on 2008-01-08
> **TechRavingMad said:**
> You could also go to nvidia's site if for some reason the restricted driver doesn't work:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

TRM

I just did it this way.

It didn't have the right one for my kernel in the package and it couldn't find it via download - so it compiled a new one...which I think is a bit off key...but in any event, it did not work, the output from **aptitude search nvivida-glx** returns the same thing, and full screen stream movies still are completely choppy and unwatchable.

I kinda refuse to believe that even though it's a piece of crap vid card it can't even view youtube videos at full screen - and yes, when small they run 100%.

---

### Post by Syndacate on 2008-01-08
Here's the link to the vid card.

[http://www.pny.com/products/verto/performance/7600gspcie.asp](http://www.pny.com/products/verto/performance/7600gspcie.asp)

It says it supports up to 2xxxX* resolution, but when I kicked it down from 1980x1200 to 1440x900 the videos were a lot smoother - I mean it doesn't really say a lot because they're not the best quality to begin with.

It seems as though I was maxing out the resolution but this simply doesn't make sense as I can view a high def movie in kaffiene player perfectly...  And since it's caching well in advance (youtube) before it plays, I don't see where the issue is coming from...

---

### Post by Syndacate on 2008-01-08
UPDATE:
I have confirmed that this IS an ubuntu only problem.  I'm running XP/Kubuntu (Ubuntu Desktop Package) dual boot system, I just booted windows and installed the drivers off Nvidia's website - at 16xx X 1050 or whatever it was it was 100% smooth, even on this that same res. is pretty shaky, and it's completely dead choppy at 1900...

:-\

Gah, I  can't be the only one with this problem.

On the flipside, it doesn't make much sense because I can watch a high def movie off an .iso or whatever and it supports it fine, 100% smooth.

I'm next ready to rule out FireFox as the culprit but Linux browsers tend to have 0 support for web apps - Anybody know which browsers can support the youtube interface correctly?  Konqueror couldn't do crap, and the other one I used (name escapes me) didn't display all of the interface, wouldn't show the maximize buttons...

---

### Post by RomeReactor on 2008-01-08
The only thing that I can think of at the moment is that your card might not be using the restricted drivers, even though they're installed; from the terminal:
```
cat /etc/X11/xorg.conf
```
and
```
glxinfo | grep direct
```
and please post the output. Do you have Compiz enabled while this problem with Flash happens?

---

### Post by Syndacate on 2008-01-08
> **RomeReactor said:**
> The only thing that I can think of at the moment is that your card might not be using the restricted drivers, even though they're installed; from the terminal:
```
cat /etc/X11/xorg.conf
```
and
```
glxinfo | grep direct
```
and please post the output. Do you have Compiz enabled while this problem with Flash happens?

Compiz is always on, yes.

**Result of "cat /etc/X11/xorg.conf":**
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

**Result of "glxinfo | grep direct":**
```

direct rendering: Yes

```

---

