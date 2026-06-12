---
title: "General 'Visuals' Issues"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Lujoki on 2007-09-07
Hi Guys, 
Ok, install has been completed successfully and I haven't used Linux before.
I have done enough reading on the xorg.conf file and all the threads and posts and none of which has helped me.
Basically I have [2 x Dell 1704FPT Flat Panel Monitors]("http://support.dell.com/support/edocs/monitors/1704fpt/EN/index.htm") and [1 Powercolor Radeon 9250 256MB DDR Video Card]("http://www.directron.com/r92uld3.html"). 
My first problem is I am unable to use any other Resolution except for "1024x768" "800x600"  and "640x480".
I wish to use dual screens at 1280x1024 but unable to achieve this.

I need someone to step me through achieving my goal as this is frustrating me and I don't want to give up.

Note: I have tried *sudo dpkg-reconfigure -phigh xserver-xorg*

```

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
        Load    "i2c"
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
        Option          "XkbLayout"     "us"
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

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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

Section "DRI"
        Mode    0666
EndSection


```

---

### Post by Ianman on 2007-09-07
I had the exact same problem in the beginning and I found that I had to manually set the correct refresh rate in my xorg.conf file. Once I did that I was able to select the right resolutions! You have to change this bit:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        [COLOR="Red"]HorizSync       28-51
        VertRefresh     43-60[/COLOR]

Just look on the manufactures site for the right values and adjusst the HorizSync and VertRefresh settings accordingly.

Hope this helps!

---

### Post by johnbull on 2007-09-07
This worked for me.
Under Section Monitor, edit the HorizSync to read 28-64
In each Screen Subsection edit the first modes entry to be 1280x1024
Save it
Ctl-Alt-Backspace (to forcel reload
You the have the 1280x1024 option oh resolution settings available

---

### Post by Lujoki on 2007-09-07
> **Ianman said:**
> I had the exact same problem in the beginning and I found that I had to manually set the correct refresh rate in my xorg.conf file. Once I did that I was able to select the right resolutions! You have to change this bit:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        [COLOR="Red"]HorizSync       28-51
        VertRefresh     43-60[/COLOR]

Just look on the manufactures site for the right values and adjusst the HorizSync and VertRefresh settings accordingly.

Hope this helps!

Thanks for your input but the issue still stands after I made those changes.
So now it looks like this...
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-76

```

I did this and restarted X Windows and nothing has changed.
What next ? :confused:

---

### Post by Lujoki on 2007-09-07
Oh wait....
after making the changes as per the previous post, i then changed the res size in each section, this worked!

Excellent.... I am part way there...

Anyone able to point me in the right direction to get my dual monitors working?

---

### Post by Lujoki on 2007-09-07
Oh, and thanks again guys for your help with that!

---

### Post by overdrank on 2007-09-07
> **Lujoki said:**
> Oh wait....
after making the changes as per the previous post, i then changed the res size in each section, this worked!

Excellent.... I am part way there...

Anyone able to point me in the right direction to get my dual monitors working?

Hi and maybe you can start here
[http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama)
Good luck!

---

### Post by ORBiTrus on 2007-09-07
ATI drivers can be extremely annoying to dual-head.  Good Luck, I know I needed it when I tried.

---

### Post by Lujoki on 2007-09-08
> **ORBiTrus said:**
> ATI drivers can be extremely annoying to dual-head.  Good Luck, I know I needed it when I tried.

So when you say tried you mean failed? :(

---

### Post by Lujoki on 2007-09-08
Can anyone tell me why I would get the following error when trying to install ATI Drivers...

./ati-installer.sh: 165: Syntax error: Bad substitution

This is after I have run sh ./ati-driver-installer-8.28.8.run as per the website instructions here...
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html)

---

### Post by Ianman on 2007-09-09
do you not have to use "sudo" to run a script?

---

