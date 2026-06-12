---
title: "ATI and composite"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-04-12
I have a question. Yeah like we all do :P. I ve installed fglrx drivers for my ATI 9600 and it works well. Now i wanted to install compiz and it says that i have composite disabled. What is this composite for? Why is it disabled by default? How can i enable it? And will anything else go wrong if i do that?

Thanks in advance!

---

### Post by AtrejuT on 2007-04-12
You'll have to install Xgl to use compiz with fglrx. Nothing will go wrong if you are lucky - but if you're unlucky you'll break your X11 leaving you with a  command-line interface only. It can be fixed though and nothing permanently should get broken!
there is a rather good tutorial here: 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
since you don't want to use beryl you can skip the step about enabling beryl repositories and installing beryl. what you need is the part about installing Xgl and adding a session for xgl.

For questions just post back here - good luck!

---

### Post by freebird54 on 2007-04-12
I think I need a little more detail to know where you are in your quest!  If you could post the output from these commands, I'd know more what to say next. From  a terminal, enter:

```
fglrxinfo
```

```
glxinfo | grep direct
```

and perhaps even

```
cat /etc/X11/xorg.conf
```

Installing the fglrx is not necessarily getting them to work right! (but it will happen)

---

### Post by Vandorius on 2007-04-12
Hey thanks for reply. I wuld be happy if u help me on this quest. But i have one more question before i install compiz. I have disabled drawing window when resizing or moving becouse if i dont i get multiple windows behind when i move they dissapear after a second or two(if u know what i mean) Its like slow refresh or something.

Ok now to my output from terminal.

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

```

```
direct rendering: Yes
```

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
        Option          "XkbLayout"     "slo"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "ATI 9600"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
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

And yeah i use 7.04 version cozz i culdnt wait for the final release :P

Thanks guys!

---

### Post by freebird54 on 2007-04-12
OK  - everything looks OK so far.  All you need is to get XGL loaded.  The link that was posted for you above should do that just fine - just go step by step, and don't load Beryl itself.  All the rest (about making a startxgl file, and a session entry) will be the same.

You'll know you have it going when after login you see a grey background with an X for a mouse pointer - before the desktop loads.

---

### Post by dstew on 2007-04-12
To enable composite video, edit your xorg.conf file. Change: 

Section "Extensions"
        Option          "Composite"     "**0**"
EndSection

to

Section "Extensions"
        Option          "Composite"     "**enable**"
EndSection

---

### Post by Vandorius on 2007-04-14
I know this is lame but.... How do i properly edit it in KDE? I wanted to do this once and i pasted Option "Composite" "enable" on the end and i guess it didnt replace. So my X didnt start next time. And cozz i lack knowledge big time i just reinstalled. So i wanna ask once again will enabling composite make something unstable? Why it isnt enabled by default? And how do i properly edit and replace that line? And the last one will compizz run on my ATI Radeon 9600 with fglrx drivers with composite enabled?

Thanks for explanation in advance!

---

### Post by igknighted on 2007-04-14
> **dstew said:**
> To enable composite video, edit your xorg.conf file. Change: 

Section "Extensions"
        Option          "Composite"     "**0**"
EndSection

to

Section "Extensions"
        Option          "Composite"     "**enable**"
EndSection

NOOOO, DO NOT DO THIS!!!

FGLRX drivers cannot handle composite.  I doubt your xserver would load if you did this, and if it did, the screen would artifact like crazy and it wouldn't be usable.  You do not need to enable composite when using XGL, just follow the guide posted above.

If XGL is intimidating (and it can be), there is an alternative.  Read this page [http://help.ubuntu.com/community/RadeonDriver](http://help.ubuntu.com/community/RadeonDriver) and this page [http://ubuntuforums.org/showthread.php?t=290841](http://ubuntuforums.org/showthread.php?t=290841) for directions on how to use Beryl/Compiz natively with AIGLX instead of XGL... much easier.  (I know the second link says Edgy, but the only thing that should change is the repo, and since Compiz is already installed on Fesity thats no issue).

---

### Post by forrestcupp on 2007-04-14
If you just use the opensource ATI drivers instead of fglrx, then you *can* enable composite in xorg.conf and use aiglx instead of Xgl.  This is a lot better if all you want is compiz.  But the opensource drivers don't support all of the features in opengl that fglrx does, which means some opengl games and other apps might not work properly.

So depending on your needs, if you need fglrx, you will have to use Xgl, and you absolutely cannot enable compositing in xorg.conf.

---

### Post by Vandorius on 2007-04-14
Thanks to stop me before the next X crash :D After reading this i ve decided that i ll wait for this thing to sort out. So it wont be so dangerous to do that. Im working with 3D so i need fglrx cozz it runs a lot better than ati driver. I just wanted to install compizz cozz it has some cool features that i culd use. But i think i ll stay with securely working desktop. Thanks anyway guys. I hope that drivers will get better trough time i just dont wanna install linux the 6 th time :P

Take care!

---

### Post by forrestcupp on 2007-04-14
Xgl will work for compiz with fglrx, but I don't think Xgl works properly with opengl applications.  You have to start a new x-session without Xgl to properly run opengl stuff.  So there's no great solution.  

I know you don't want to hear this, but I just sold my geforce card on ebay so that I can get an nvidia card.  Nvidia supports Linux way better.  I can use their binary drivers with aiglx without messing with Xgl, and compiz just works along with any opengl app I want to run.  I couldn't get my ATI card to work in a good enough manner no matter what I did.  Nvidia takes away all of the headaches.

---

