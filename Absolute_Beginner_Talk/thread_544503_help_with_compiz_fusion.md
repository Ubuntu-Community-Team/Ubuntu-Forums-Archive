---
title: "help with compiz fusion"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-09-06
I used the following guides:

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

nothing worked, I typed 'compiz' in terminal:

```
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

I typed 'lspci' in terminal:

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
05:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

any ideas? I followed both faqs to the letter.  Thanks for reading.  

P.S. my video card is a 7800gt. I went to System > Administration > Restricted Drivers Manager as the faq told me, and it shows my driver enabled and in use (NVIDIA accelerated graphics driver).  However, it does say 'In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported.'

---

### Post by Sqwishy on 2007-09-06
try
compiz --replace

also if you're trying to use emerald you might need to run
compiz --replace -c emerald

---

### Post by igknighted on 2007-09-06
type "compiz --replace"

You need the --replace option because there is already a WM running (metacity)

---

### Post by alwiap on 2007-09-06
i typed 'compiz --replace' in terminal

```
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5991): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

i forgot to mention i had 'compiz --replace' in System > Preferences > Sessions as the faq told me.

still not working however.

---

### Post by igknighted on 2007-09-06
did you run this command?

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by alwiap on 2007-09-06
yes, i used that command in terminal when I was setting it up in the faq.

ran it again, seemed fine:

```
Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

:(

---

### Post by igknighted on 2007-09-06
> **alwiap said:**
> yes, i used that command in terminal when I was setting it up in the faq.

ran it again, seemed fine:

```
Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

:(

Can you post your xorg.conf?

---

### Post by alwiap on 2007-09-06
how do i do that? im a nub.

thanks for your help much appreciated.

---

### Post by alwiap on 2007-09-06
nevermind, think i found it.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
    Identifier     "A90f+"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "A90f+"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by BobCFC on 2007-09-06
I think the key error is "symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity"

The others are just warnings.. a google search turns up this error on the big [54page thread]("http://sudan.ubuntuforums.com/showthread.php?t=481314&page=4") about compiz

> I had the same problem. The libdecoration0 package needs to be upgraded too. Just do a search in Synaptic for libdecoration and upgrade it.

and on the next page

> Upgrade from Synaptic your libdecoration to version 0.5. After that effects should work.


> I had the same problem, and that fixed it! Everything works now but the desktop cube


That was from june so it may be even newer version than 0.5

Hope this helps

---

### Post by AlexenderReez on 2007-09-06
> **alwiap said:**
> yes, i used that command in terminal when I was setting it up in the faq.

ran it again, seemed fine:

```
Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

:(

you need to restart xserver after run that command....

---

### Post by igknighted on 2007-09-06
Add this section at the end of the file:

```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

You might need to explicitly tell it to load dri module too, but I would try adding the first part before anything else.

---

### Post by alwiap on 2007-09-06
how do i edit xorg.conf since it is read only? is there a terminal command?

---

### Post by igknighted on 2007-09-06
```
gksudo gedit /etc/X11/xorg.conf
``` (for gnome)

---

### Post by arashiko28 on 2007-09-06
Did you ever used Beryl before installing compiz fusion? Because as far as I know (not much but enough), it won´t run if you keep having Xgl not present as it shows your posts. It is supposed to show OK... only this way supports Beryl and CF don't know, just wonder...

---

### Post by alwiap on 2007-09-06
No I did not use Beryl before.

I put in ```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

in xorg.conf

and restarted, nothing changed.

Also I noticed that there are no icons on my desktop and that when i left-click my mouse on the desktop, when you usually get a box that drags with you, I get nothing.

---

### Post by alwiap on 2007-09-06
i uninstalled everything, and reinstalled with the expection of not including emerald or anything else, and it works.  have no idea why, thanks for the help though.

---

