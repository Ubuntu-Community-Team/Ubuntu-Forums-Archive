---
title: "Hu?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-04-21
Hi, i just installed beryl and the top of my windows disepared:confused: 
The top were the  X wich closes windows is, you know the orange one. how do i get that back?

---

### Post by caffienefree on 2007-04-21
Right click on the beryl icon, and select reload window decorator. If that doesn't work, we can troubleshoot further.

---

### Post by ajmannen on 2007-04-21
No, didn't work:(

---

### Post by caffienefree on 2007-04-21
Are you using AIGLX or XGL?

---

### Post by ajmannen on 2007-04-21
I don't know, lol. 
I have Nvidia ge force 7300 and AMD turion 64 x2 

But i have seen that there is some settings in beryl that does this. any one know what settings?

---

### Post by bulldog on 2007-04-21
Did you install emerald and emerald-themes?

---

### Post by ajmannen on 2007-04-21
Yes

---

### Post by caffienefree on 2007-04-21
Make sure you have
> 
Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

in your Screen section of /etc/X11/xorg.conf.

EDIT: also, restart your X server.
ctrl+alt+backspace

---

### Post by ajmannen on 2007-04-21
Didn't work:(

---

### Post by ComplexNumber on 2007-04-21
and what happens when you click on the red icon in the notification area and switch back to metacity?

---

### Post by ajmannen on 2007-04-21
Then everty thing becomes normal, i get the top line :) 
But i want beryl

---

### Post by crimesaucer on 2007-04-21
I had a similar problem, so I just reinstalled in Terminal with:

```
sudo apt-get install beryl beryl-manager


``` 

then I re-started it up with:

```
beryl-manager
```

Then my icon and Beryl Manager came back since it had disappeared in the upgrade to 7.04.

So did my Emerald.

---

### Post by ajmannen on 2007-04-21
Didn't work either :(

---

### Post by ajmannen on 2007-04-21
when i tryed to install beryl now i got this messege
> * Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
Initiating splash
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


---

### Post by crimesaucer on 2007-04-21
I don't have NVIDIA so I'm not sure how to help, good luck.

---

### Post by bulldog on 2007-04-21
You have to set the default depth to 24 in your xorg.conf.
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
```

---

### Post by orb9220 on 2007-04-21
Does your xorg.conf have 32 bit for depth?

> beryl: No GLXFBConfig for depth 32

error says you are not set at 24bit do as bulldog says look for the screen section and make sure you have.

 > DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"

---

### Post by ajmannen on 2007-04-22
[PHP]andreas@andreas-laptop:~$ Section "Screen"
bash: Section: command not found
andreas@andreas-laptop:~$     Identifier     "Default Screen"
bash: Identifier: command not found
andreas@andreas-laptop:~$     Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
bash: Device: command not found
andreas@andreas-laptop:~$     Monitor        "Generic Monitor"
bash: Monitor: command not found
andreas@andreas-laptop:~$     DefaultDepth    24
bash: DefaultDepth: command not found
andreas@andreas-laptop:~$     Option         "AddARGBGLXVisuals" "True"

[/PHP]

Hu?

---

### Post by caffienefree on 2007-04-22
sudo gedit /etc/X11/xorg.conf

Scroll down to section screen and add the entry the previous poster suggested. Save, close the text editor, hit ctrl+alt+backspace, and log back in.

---

### Post by ajmannen on 2007-04-22
Here is the defult code [PHP]Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection
[/PHP]
In bulldogs code is a difrent graphic card then i have, thats all. i have Nvida GeForce Go 7300 128 Mb

---

