---
title: "Font &amp; overall graininess/bluriness?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by caaqayuush on 2006-11-02
Hello, 

I am hoping someone can help me with this. I am a new user (just recently installed 6.10) and I am having a problem where all the fonts appear to be grainy or blurry. I have tried messing around with System-Preferences-Font and I can get minimal gains in quality but it still doesn't look right. I have a feeling that it might be the proprietary NVidia driver but I am not sure. I got the driver using Automatix2. Some other related problems I get is occasional letter overlapping,  and things like bullets and buttons are also grainy or jagged. There is a screenshot link at the bottom of this post as well. 

Specs: 
Graphics Card: Nvidia 7800gs
LG 20.1" Widescreen LCD (running 1680x1050 resolution)

xorg.conf

> Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-84
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

Here is a screenshot so you can get a sense of what I am looking at. 
[[IMG]http://img76.imageshack.us/img76/2121/grainynessmk2.th.png[/IMG]](http://img76.imageshack.us/my.php?image=grainynessmk2.png)

---

### Post by theicyj on 2006-11-02
This is probably a stupid question but have you tried changing the current "Documents Font" in System -> Preferences -> Font to something like Sans?

Another thing I noticed is that your uglier fonts are showing up in amsn and notepad running on wine.  In order to change the font in notepad, I think you have to change some setting in wine and one of the reasons I don't like amsn is because that application for some reason doesn't seem to use the system font.

---

### Post by caaqayuush on 2006-11-02
Documents Font is already set to sans, I still get weird bluriness on that as well...

---

### Post by thekid on 2006-11-02
> **caaqayuush said:**
> Documents Font is already set to sans, I still get weird bluriness on that as well...

yea i am having the same problem. I hate this font. I  wanna go back to 6.06 :(

shouldn't have upgraded it

---

### Post by thekid on 2006-11-02
> **caaqayuush said:**
> Documents Font is already set to sans, I still get weird bluriness on that as well...

I even tried changing the font redering option.. ahh, i hate this!!

---

### Post by caaqayuush on 2006-11-03
Well at least I am glad to see that someone else is on the same boat as me... Any help in solving this matter would be greatly appreciated!

---

### Post by caaqayuush on 2006-11-08
Well it's been 5 days now, figure its time to bump this...

---

### Post by caaqayuush on 2006-11-08
Well I think I may have found what the problem may be but I am unsure how to fix it. My monitor tells me that the resolution is set at  1280x1024 while System-Preferences-Screen Resolution tells me that my resolution is set to 1680x1050. I went into my xorg.conf and removed all resolutions except 1680x1050, and also added in the refresh rates for my monitor, then I restarted, and it is still happening. Any suggestions?

---

### Post by caaqayuush on 2006-11-11
Been a couple days since my last post, figured I'd bump this once again.

---

### Post by balaram on 2006-11-11
I was having problems too but installing the new nVidia drivers solved it now everything looks good. Have you already done this?

---

### Post by caaqayuush on 2006-11-11
Yeah I have the new drivers as well. Problem is still happening. :(

---

### Post by caaqayuush on 2006-11-13
Okay, I've tried reconfiguring X and it made no difference. I look in xorg.conf and I notice that it doesn't recognize my monitor? Which is  an LG Flatron Wide L204WT. Any suggestions anyone?

---

### Post by akao on 2006-11-13
I believe your problem has to do with fond rendering.  I just moved to 6.10, and am trying to solve the problem myself.  First off, it seems like your hinting is turned down, which you can turn up in the preferences > font.

The other issue, if I remember correctly, is that small fonts should not be anti-aliased, as they are already quite small and no need to make them look a blurry mess.  I'm currently trying to find out how to do that.  I remember when I went through this before, there were quite a few forum threads on the topic.

Cheers.

---

### Post by caaqayuush on 2006-11-13
Actually my hinting is on full, although as it is turning it off doesn't seem to make it look much less worse. Friend of mine was saying he thinks it is my video drivers... But I don't know. I noticed that in my xorg.conf file my video card and monitor arent shown... I am using Nvidia 7800GS with LG L204WT monitor... Adding in the correct horiz and vert refresh rates did nothing to solve my problem either.

---

### Post by caaqayuush on 2006-11-13
I tried setting Ubuntu to 1280x1024 resolution. In this resolution my fonts look perfectly fine, however it is not a widescreen resolution... :( Then I put it back to 1680x1050 and everything looks like crap once again and my monitor says that the signal it is getting is only 1280x1024

---

