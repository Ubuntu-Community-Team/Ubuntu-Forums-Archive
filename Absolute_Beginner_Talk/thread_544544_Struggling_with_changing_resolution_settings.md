---
title: "Struggling with changing resolution settings"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by mpower on 2007-09-06
First of all, apologies for a thread that I know has been done to death on here....trouble is I just can't get the proposed solution to work.

I've just installed Ubuntu (first time Linux user btw..) and get just the 3 settings for resolution, the highest being 1024 x 768. I want to set it at 1440 x 900 though.

I've entered the command line "sudo dpkg-reconfigure xserver-xorg" and had the configuration tool open...gone through all the settings, making sure to include the 1440 x 900 option in the resolution list. Saves it to the file, I restart with Ctrl-Alt-Backspace but...

1024 x 768. Every time :(

It's really driving me a bit mad (that you should even have to go through such a process simply to get the right resolution is pretty annoying tbh).

So...anyone that's not sick of covering this topic that would kindly take some time to help me out...I'd be very grateful. Cheers, Mark

---

### Post by mikewhatever on 2007-09-06
Can you post the output of the following command from the terminal:
> cat /etc/X11/xorg.conf

---

### Post by mpower on 2007-09-06
Yep...

As you can see, 1440 x 900 is on the list...
------------------------------------------------

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI RADEON"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Acer"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON"
        Monitor         "Acer"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

---

### Post by mikewhatever on 2007-09-06
Have you tried setting the default depth to 16? DefaultDepth 16 instead of DefaultDepth 24.

---

### Post by mpower on 2007-09-06
Hey Mike

I've actually managed to sort it out. It's meant me installing the 'unsupported driver' but the simple fact is that as soon as I installed it everything was OK....so unsupported or not I can live with that.

I'm now a much happier *NEW* Ubuntu user and looking forward to seeing what's available in this OS.

Thanks for taking the time to help though....much appreciated.

---

