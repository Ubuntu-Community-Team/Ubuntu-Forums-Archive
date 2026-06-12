---
title: "Help Noob - Changing Graphics card (NVidia from Onboard)"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by LadyFox on 2007-03-09
Hello, 

I'm new to this forum, so go easy ... 

Im running Ubuntu 6.10 and want to add a NVidia FX5500 VGA (currently running i810 onboard VGA in my Dell 3000 Dimension).  Ubuntu works fine with the onboard, but i want dual screens and Beryl running :)  Hence the need for a better VGA

I tried simply adding the PCI NV card but it didnt disable the onboard card/drivers.  I tried doing it in BIOS but the option wasnt there.  With the NV card in, my dual monitors both worked, but i get the Xserver screen (on both monitors).  Tried editing xorg.conf but cant seem to get it working - it has always come up with the red 'FAIL' when i have tried it before. Even after rebooting and startx .  Ubuntu refuses to start up - its like its still pointing at the i810, and i dont know how to change it. 

Can anyone help in laymans terms on what my next steps are?  (currently back on i810 with one monitor - nv card is removed and here beside me)

If i change the card then boot up - it wont boot into Ubuntu.  Can i install all the NV drivers and run the ./beryl-install-script, THEN shut-down and add the NV card?  or do i HAVE to make the changes in dpkg-reconfigure xserver-xorg?  I'd rather not do the latter as i cant seem to figure it out 

ANY advice would be fab, i'm determined to get Ubuntu running as it should do. 

Cheers!

---

### Post by jem7v on 2007-03-09
Where did you look in your BIOS? For me, it's under Integrated Peripherals or something like that... It might be worth finding out what motherboard your computer uses and looking it up on Google to see if you can find a manual for it to figure out how to disable your onboard video.

As for the drivers, you'll probably have to edit /etc/X11/xorg.conf to change the Device: Driver: from whatever it is now to either nv (for the by-default included open source NVidia drivers without hardware accelleration) or nvidia (if you have the proprietary driver installed already). It might be good to start with the nv driver just to make sure your card is functional before you install the nvidia one, because sometimes the nvidia driver can be fussy while you're trying to get it working, but nv should work almost no matter what.

---

### Post by LadyFox on 2007-03-09
Thanks Jem 

Chnaging the driver to nv, can i just go to /etc/X11/xorg.conf in the file browser, open it up and edit it there, then shut down, insert my NV card and see if it boots up?  Or change the card and edit xorg.conf through dpkg-reconfigure?

Sorry to be do dense ... :)

---

### Post by Crooksey on 2007-03-09
```

sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xocnfig
sudo gedit /etc/X11/xorg.conf

```

Now find the device section and add 

```

Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string"

```

Or.. you can use my nvidia xorg.conf thats setup for 2x 19" monitors and beryl...

```

# Crookseys xorg.conf for two 19" monitors at 1280x1024 running nvidia and beryl

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
    Option         "XkbLayout" "gb"
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


    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"           
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               
EndSection

Section "InputDevice"

    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               
EndSection

Section "InputDevice"


    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"              
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
        Identifier     "NVIDIA Corporation NVIDIA Default Card"
        Driver         "nvidia"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "string" 
	Option "RenderAccel" "True"
	Option "RandRRotation" "True"
	Option "DisableGLXRootClipping" "true"
	Option "BackStoring" "True"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection


```

Enjoy :)

---

### Post by jem7v on 2007-03-09
If you just open xorg.conf from the file browser you won't be opening it with administrative priveledges and you won't be able to save it... hence why we use
```
sudo nano /etc/X11/xorg.conf
```
to edit it instead.  nano is a command-line text editor.  Make your edit and then exit with Ctrl+X, choose Y to save it, and just hit enter to choose the file name.

You can certainly try editing xorg.conf and then putting in your new card! As long as you disable the onboard video first it should work.  And if it doesn't and you get an X server error screen, do this: Ctrl+Alt+F1 will take you to a terminal where you can log in and edit the xorg.conf file back to the original driver and use your onboard video while you troubleshoot what went wrong.
(Ctrl+Alt+F(1-6) will take you to any one of six terminals at pretty much any time. F7 is where your desktop environment (such as Gnome or XFCE or KDE) usually runs.)

---

### Post by LadyFox on 2007-03-10
Thanks guys for all your help!

Now running with twin screens, both running off the NV card!  Had to figure out how to change the left-> right direction of the cursor but otherwise its all running fine!  Thank-you!

I'm sure ill be back with more questions once i start to tackle Beryl! 

Im so glad i found this forum, a mine of information and super quick responses! Ta!

---

