---
title: "Screen Resolution looks incorrect"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Oziyak on 2007-03-06
Hi everyone,

I'm totally new to linux but really want to get away from windows.  I'm sick of it all.

so I tried installing my nvidia drivers on ubuntu with some success.  I have the resolution now at 1280x1024, however the fonts and images look stretched out.... as if the resolution is incorrect?

is there something I've done wrong?  anyone have any idea for me

sorry if this is a really newbie type of question
video card is nvidia 6600
monitor is NEC Multisync fp1350x

but this is what my xorg.conf looks like: (hope this helps with any discussion)

thanks

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
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

---

### Post by kolinab on 2007-03-07
I don't know too much about dealing with these kinds of problems BUT I did a quick search on your monitor and I'm told the max resolution for that monitor is 1920 X 1440. Is that ridiculously high? I dunno. But I think you might want to explore that avenue. There might be a way to bump it up to the max and it just might make you happy!

K

---

### Post by Oziyak on 2007-03-07
I definatly think that's pretty high and would be totally happy with my 1280x1024 except for this stretched out effect I"m experiencing....

I'm not sure if it's the video card drivers... or the monitor setup

to be honest I dont' know much of what I'm setting up here at all... lol

I'll keep my fingers crossed as I poke around

thanks

---

### Post by samadams on 2007-03-07
I'm having resolution problems too but the other way around - ubuntu won't allow me to set higher than 1024x768.  But I did notice that since I use a different resolution in XP (1152x864) the monitor itself displays the screens differently.  I have to use the monitor's adjustment controls to resize the screen or move it around so it looks right.  Perhaps this is the problem?

---

### Post by mgmiller on 2007-03-07
When you say the images are stretched out, are they not filling the entire screen?  This is a common problem with CRT monitors.  You need to use the front panel controls on the monitor itself to make it properly fill the screen at the resolution and refresh rates you are running.   The amount of screen that is filled will vary with the refresh rates chosen and will require a manual readjustment of the screen each time.  The good news is that with a multisynch monitor, the monitor itself will remember these settings once you make them, so if you change resolutions around afterwards, it should look ok.  This behavior exists in Windows as well as Linux.  It is not OS specific.

One other thought, in Ubuntu, look in System>Preferences>Screen Resolution and see if the refresh rate drop down gives you more choices.  Simply selecting a different refresh rate may get your monitor to display correctly.

---

### Post by chaplanger on 2007-03-07
My guess is that you have a widescreen display.  If this is so, 1280x1024 will look stretched out.  To get the image you want try 1680x1050 resolution.

Hope this helps!

---

### Post by mgmiller on 2007-03-08
> My guess is that you have a widescreen display. If this is so, 1280x1024 will look stretched out. To get the image you want try 1680x1050 resolution.

I don't think so.  I looked up his monitor, a NEC Multisync fp1350x, and it is a normal aspect ratio CRT.   The resolution you suggest is for a wide screen LCD, and will look distorted on this monitor.

---

### Post by chaplanger on 2007-03-08
> **mgmiller said:**
> I don't think so.  I looked up his monitor, a NEC Multisync fp1350x, and it is a normal aspect ratio CRT.   The resolution you suggest is for a wide screen LCD, and will look distorted on this monitor.

That was the purpose of the "If that is so" line.  

BTW: NEC Recommended resolution is 1,600 x 1,200 with an 85 MHz refresh rate, ensuring your graphics will maintain the flicker-free perfection you demand. (from [http://www.amazon.com/NEC-MultiSync-FP1350X-Totally-Monitor/dp/B000056SMP)](http://www.amazon.com/NEC-MultiSync-FP1350X-Totally-Monitor/dp/B000056SMP)).  It might be worthwhile giving this resolution a try at least.

---

