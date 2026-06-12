---
title: "Issue with Nvidia drivers (?)"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by WanderingKnight on 2007-05-02
Hello, I'm posting what I think is an issue regarding Nvidia drivers.

I'm running Ubuntu 7.04. I'm having two issues: The first and most noticeable one, is that enabling Desktop Effects makes all window title bars disappear, and makes windows unmovable. This happened after I messed around with the nvidia drivers (notice that I moved to Linux only 4 days ago, this is my first time out of Mac OS and Windows). The second issue (the one that bothers me most) I'll explain it further ahead.

When I installed Ubuntu, I didn't know if my Nvidia graphics card drivers came packaged in. I mostly figured they didn't, but even then, the Desktop Effects feature was completely functional. And I actually *don't* remember whether they were installed or not when I went to check that at the Add/Remove Applications feature. What I remember is that, in the application description, it said "To enable the driver, run sudo nvidia-glx-config enable". I ran that command, and I think it was then that my problems arose. After that, I saw I couldn't initialize the graphic environment in normal mode, so I got a few guidelines for editing the xorg.conf, and that made it functional. Desktop Effects were active, but the cubic workspace wasn't working properly. It was then that I started to notice that, even though the Power Management feature was configured so that the display would power off after 40 minutes of inactivity, it only needed about 10-15 minutes to power off. Not only that, but when it does, it screws up my color control configuration in nvidia-settings (mostly, it turns them back to default--accessing nvidia-settings fix this). I tried messing around further, but that only led to the non functioning of Desktop Effects, and the other issue was still there.

Any idea how to fix this? I'm pretty, pretty sure I had the drivers installed back when I had my fresh Ubuntu installation (how the hell could I run normally the graphic environment, anyways?).

Oh, I don't know if this is normal, but my xorg.conf lists my graphic device as "generic device". My card is an FX5200.

---

### Post by igknighted on 2007-05-02
> **WanderingKnight said:**
> Hello, I'm posting what I think is an issue regarding Nvidia drivers.

I'm running Ubuntu 7.04. I'm having two issues: The first and most noticeable one, is that enabling Desktop Effects makes all window title bars disappear, and makes windows unmovable. This happened after I messed around with the nvidia drivers (notice that I moved to Linux only 4 days ago, this is my first time out of Mac OS and Windows). The second issue (the one that bothers me most) I'll explain it further ahead.

When I installed Ubuntu, I didn't know if my Nvidia graphics card drivers came packaged in. I mostly figured they didn't, but even then, the Desktop Effects feature was completely functional. And I actually *don't* remember whether they were installed or not when I went to check that at the Add/Remove Applications feature. What I remember is that, in the application description, it said "To enable the driver, run sudo nvidia-glx-config enable". I ran that command, and I think it was then that my problems arose. After that, I saw I couldn't initialize the graphic environment in normal mode, so I got a few guidelines for editing the xorg.conf, and that made it functional. Desktop Effects were active, but the cubic workspace wasn't working properly. It was then that I started to notice that, even though the Power Management feature was configured so that the display would power off after 40 minutes of inactivity, it only needed about 10-15 minutes to power off. Not only that, but when it does, it screws up my color control configuration in nvidia-settings (mostly, it turns them back to default--accessing nvidia-settings fix this). I tried messing around further, but that only led to the non functioning of Desktop Effects, and the other issue was still there.

Any idea how to fix this? I'm pretty, pretty sure I had the drivers installed back when I had my fresh Ubuntu installation (how the hell could I run normally the graphic environment, anyways?).

Oh, I don't know if this is normal, but my xorg.conf lists my graphic device as "generic device". My card is an FX5200.

Sounds like your graphics drivers are working fine, but you forgot to enable ARGBGLXVisuals.  I will recommend you check out the website [www.beryl-project.org](www.beryl-project.org).  If you look at their wiki there is a much better way than using Ubuntu's "Desktop Effects" option.  This should give you your titlebars/window decorations back.  Just disable the "desktop effects" and follow that guide.

Also, to be 100% sure your video drivers are working other than the ARGBGLX thing, try running the commands 'glxinfo | grep direct' and 'cat /etc/X11/xorg.conf' and post back what the results are (the cat command will be quite long).

EDIT: The generic device thing is normal.

---

### Post by WanderingKnight on 2007-05-03
The glxinfo command said display is fine, here is the info from the other command:

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
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
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
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


The thing I want isn't getting Desktop Effects back. I want that awful "auto-reset" thing of the color controls to go off. It's extremely bothering because it also happens when I'm running a fullscreen application. It doesn't turn off the display, but resets the color adjustment to its default (though when I open nvidia-settings it's still as I left it and it's reset back immediately).

---

