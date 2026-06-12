---
title: "Easiest way to dual monitor"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by aajvs99 on 2007-03-04
Hello all this is my first post. Im no new comer to ubuntu its been my favorite distro for a long time. anyway me and a friend are both switching from our former OS's mine XP his macOSX to ubuntu as our main os for normal computing (Office, internet, music, school, email etc.) We both still need our originals for other operations. anyway in XP its really easy to setup dual monitors but in ubuntu i cannot figure it out at all heres my setup

AMD Athlon 3200+ 2.0GHZ
1GB PC3200 RAM
20GB HD <--For Ubuntu
250GB HD
[INDENT]-75GB for XP (i use it to game)[/INDENT]
[INDENT]-125GB for Files [/INDENT]
[INDENT]-Both are mounted in linux so i can easily transfer files[/INDENT]
nVidia 7600GT 256mb (yes i have the nvidia drivers installed
2 19" Viewsonic CRT's that i want to dual with

im running Beryl currently which is really fun way better than anything you can do in windows anwyay if anybody can show me a really easy way to get a Span setup running that would be awesome.

---

### Post by Scunizi on 2007-03-12
Here's what I use to use for my dual monitor setup.  I had/have a 6600gt 256m card with 1 dvi out and one vga out.  The setup should be essentially the same.  I don't know if Byrl will like it or not but might be worth a try.  Use the basic layout changing the values where needed.

> Section "ServerLayout"
 Identifier	"xinerama"
 Screen	0 "Screen0"
 Screen	1 "Screen1" RightOf "Screen0"
 InputDevice    "Generic Keyboard"
 InputDevice    "Configured Mouse"
 Option "Xinerama" "1"
EndSection

Section "Files"

 # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
 FontPath        "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/Type1"
 FontPath        "/usr/share/X11/fonts/100dpi"
 FontPath        "/usr/share/X11/fonts/75dpi"
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
 Option         "XkbModel" "pc104"
 Option         "XkbLayout" "us"
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

Section "Extensions"
 Option "Composite" "Enable"
EndSection


Section "Monitor"
 Identifier	"Envision"
 Option	"dpms"
 HorizSync 30.0-81.0
 VertRefresh 56-75
EndSection

Section "Monitor"
 Identifier	"HSD HN199D"
 Option	"dpms"
 HorizSync 30.0-98.0
 VertRefresh 50-160
EndSection

Section "Device"
    Identifier  "Nvidia0"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       0
 #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "CRT"
    Option "UseDisplayDevice" "CRT"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    #Option "AllowGLXWithComposite" "true"
    Option "NvAgp" "3"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Device"
    Identifier  "Nvidia1"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       1
    #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "DFP"
    Option "NvAgp" "3"
    Option "UseDisplayDevice" "DFP"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    #Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device	"Nvidia0"
    Monitor	"Envision"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1024x768" "800x600"
    EndSubsection
EndSection

Section "Screen"
    Identifier	"Screen1"
    Device	"Nvidia1"
    Monitor	"HSD HN199D"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection


---

### Post by kerry_s on 2007-03-12
install the nvidia driver and in terminal->
sudo nvidia-xconfig --twinview
reboot

---

