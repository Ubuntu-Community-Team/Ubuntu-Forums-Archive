---
title: "Feisty Fawn-NVidia 6600GT spontaneous reboot"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-05-25
Hello all,
Think I might have a problem with my graphics system somewhere. System specs are:
..Pentium 4 2.6 gHz
..I gig RAM
..NVidia GeForce 6600GT (128mB)
..Ubuntu 7.04 with all updates installed (including a recent update for the NVidia card)
..Beryl/Gnome desktop

My xorg.conf file has (after all the header/commented-out stuff):
```
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
    # 1280x960 96dpi
#    DisplaySize    270    203    # 1024x768 96dpi
#    DisplaySize    338    254    # 1280x960 96dpi
#    DisplaySize    338    270    # 1280x1024 96dpi
#    DisplaySize    370    277    # 1400x1050 96dpi
#    DisplaySize    423    370    # 1600x1400 96dpi
    Identifier     "Hitachi CM753ET"
    DisplaySize     338    254
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVidia GeForce 6600"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "True"
    Option "AllowGLXWithComposite" "True"
    Option "backingstore" "True"
    Option "TripleBuffer" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVidia GeForce 6600"
    Monitor        "Hitachi CM753ET"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

It doesn't matter whether my Window Manager is Beryl or Metacity (the Gnome default) - the behaviour persists. The reboots generally occur when I'm running the following programs:
Firefox (most often)
Evolution (occasionally)
Mahjongg (frequently)

The reboot is not a complete unload of Linux - it just places me back at the login screen, so I kinda think it's an XWindows issue... has anyone else encountered this in Feisty Fawn? This never happened in Ubuntu 6.10, for some reason - hasn't been a problem until I did the update. Also, once this happens, and if I just log in again, it will do it again fairly quickly and won't stop rebooting until I shut the system down and restart from shutdown.

Any ideas?

Cheers,
Robyn

---

### Post by jiminycricket on 2007-05-26
Have you tried replacing "nvidia" (under Section "Device") with "nv" or "vesa"?  It may be a bug in the nVidia proprietary driver.

The only thing is that nv and vesa may not support your card since it's newer...sigh.  Do you see any errors under ~/.xsession-errors ?

---

### Post by Robynsveil on 2007-05-28
> **jiminycricket said:**
> Have you tried replacing "nvidia" (under Section "Device") with "nv" or "vesa"?  It may be a bug in the nVidia proprietary driver.

The only thing is that nv and vesa may not support your card since it's newer...sigh.  Do you see any errors under ~/.xsession-errors ?

Apparently, I'm not meant to do that - I do have the Restricted Drivers manager handling the driver:
[IMG]http://www.tightbytes.com/images/ubuntu/RDScreen.jpg[/IMG]

My ~/.session-errors for just today has the following entry:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "robyn"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
SESSION_MANAGER=local/Flight:/tmp/.ICE-unix/5726
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/robyn/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
evolution-alarm-notify-Message: Setting timeout for 56413 1180447200 1180390787
evolution-alarm-notify-Message:  Wed May 30 00:00:00 2007

No idea what any of that means, tho... and thanks in advance for giving me ideas on how to fix it!

---

### Post by Robynsveil on 2007-05-31
For those of you who might be remotely interested in the cause of the spontaneous reboot, I'm leaving this little update. My conclusion here on the cause of the reboot is based on the fact that when I made a change in the BIOS, the re-booting problem went away... so I do *not* have conclusive evidence that I *have* discovered the problem and fixed it.

In any event, I had noticed during boot-up that the PC seemed to stall - longer than normal - before bringing up the little menu to select which OS to boot to... and it seemed to be searching for an OS on the DVD reader/writer.  The problem had been annoying me on the DVD reader, and had become quite pronounced when I upgraded from a DVD reader to a DVD re-writer. I decided that there was no real reason for the 1st boot drive to be something other than the HDD, so I made the change in the BIOS, and viola! no more spontaneous reboots.

Cause and effect? I kinda think so, but I might be wrong. I was loathe to go on record as stating that the problem was solved, but it's been several days now since I've had the problem, and I've been doing graphics-intensive stuff, so I kinda think maybe this might be it.

Interesting.

And here I thought the problem was with the graphics system, when all the time it had to do with Linux trying to read the DVD drive or something. Wiser minds than mine probably have a far better explanation why this would be - feel free to jump in here anytime, Wiser Minds... :D

I'm just glad it's fixed... at least, I'm pretty sure it's fixed... ;)

---

### Post by pappapump on 2007-05-31
Removing the boot from CDrom will definitely speed things up.
Also remember that if a CD happens to be in the drive at reboot that it will look for a startup file and bootable image.
This process is delayed even further if the CD in the tray happens to be a DVD.
BTW your Restricted driver window looks like the older version.
I only get the agere modem selection on the outdated Nvidia restricted driver install.

---

### Post by Robynsveil on 2007-06-04
> **pappapump said:**
> ...BTW your Restricted driver window looks like the older version.
I only get the agere modem selection on the outdated Nvidia restricted driver install.
I do updates automatically - you know, that little orange star that shows up periodically?  - is there some way to update this manually?

---

