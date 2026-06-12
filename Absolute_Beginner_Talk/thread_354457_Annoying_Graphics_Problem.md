---
title: "Annoying Graphics Problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by naoise on 2007-02-06
Ok, so I tried to follow the nvidia graphics install after a fresh install of edgy, and now my screen went to a shade of blue all over and i can't figure anything out since this was the first thing i've done in linux, pleasssssee help!

I have a 7800gt.

---

### Post by rsambuca on 2007-02-06
what instructions did you follow?

---

### Post by naoise on 2007-02-06
sudo aptitude install nvidia-glx
sudo nvidia-xconfig

then restarted knome.

i'm reaaaaaaaaaaaally confused. stupid ex-windows :(. i just want it to look ok, then it goes blue. if i can manage beryl, will it look prettier than what i'm seeing after a fresh install, or do i just have to config? I'm looking for 1280 WS ..

Thank you so much!

---

### Post by naoise on 2007-02-06
bump. Really...someone HELP...this is awful. Does anyone know why this could have happened and how to fix it?

---

### Post by Mba7eth on 2007-02-06
remove all ur nvidia driver completly 
```

$sudo aptitute purge PACKAGE_NAME 
```
Then take alook [at this ]("http://albertomilone.com/projects.html")
follow the instuction ;)

---

### Post by naoise on 2007-02-06
ack, and how do i know the package name?

---

### Post by Spr0k3t on 2007-02-06
nvidia-glx, as stated from your prior post.

---

### Post by dcstar on 2007-02-06
```
sudo gedit /etc/X11/xorg.conf
``` and change the "nvidia" to "nv".

Then CTRL-ALT-BACKSPACE to restart the X server.

That should run the basic Nvidia driver instead of the one that doesn't seem to work.

---

### Post by ndefontenay on 2007-02-06
After I've installed kubuntu, I got a lot of noise in black areas of my pictures.
I've decided to install a newer nvidia driver and used envy application. (which is a great tool by the way).

The installation with the help of envy went really smoothly but never solved my noise problem on pictures and anything that gets dark colors be it a movie or a picture.

Did anyone face this problem before?

---

### Post by naoise on 2007-02-06
Ok, so I done messed up real good. Now it can't even boot to X, it just gives a nice long message and a very ugly screen. I can get to non-GUI, but i don't know what to do. I deleted the file, and am now stuck w/o graphics..

---

### Post by naoise on 2007-02-06
correction. X is back up...i fixed it by reinstalling the file and enabling the config. But its still blue! Why on earth? Should I switch to the legacy driver? Im on an AMD 4400 w/ nvidia 7800. 

thanks.

oh right...and my display is a TV

---

### Post by rsambuca on 2007-02-06
OK, let's start at the beginning here.  Try cutting and pasting the following.

1.  Install your nVidia driver.
```
gksudo gedit /etc/apt/sources.list
```
In the window that opens up, add the following repository
```
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
```
Save and exit.
Next, in a terminal
```
sudo echo && wget http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
Then
```
sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx
```

2. Configure your X.org to use the driver:
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Now restart X (<Cntrl> <Alt> <Backspace>) or reboot

We'll worry about Beryl installation after you get this working!

---

### Post by naoise on 2007-02-06
hell yes, thank you. i'm doing this now. So I guess the next thing is to fix my resolution...cuz this is wayyyy to hard to read from 7 feet away.

---

### Post by rsambuca on 2007-02-06
So this worked?  

Next questions:  What are your TV specs?  ie, 1080p, 1080i, 768p, 720p?
LCD, DLP, etc?
What is your connection to the TV - DVI, HDMI, VGA?

---

### Post by naoise on 2007-02-06
Actually, I restarted and it went back to the blue hue that seems unfixable. It was fine and back to normal before though, this sucks. 

Should i edit config back to nv?

The TV is 720P LCD via Compositie.

---

### Post by rsambuca on 2007-02-06
It sounds like the PC is sending an incompatible resolution to the TV.  Can you post the output of your xorg.conf?
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by naoise on 2007-02-06
Ya i just started reading something on the nvidia forums about this.... [http://www.nvnews.net/vbulletin/showthread.php?t=84545]("http://www.nvnews.net/vbulletin/showthread.php?t=84545")

here is the output

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
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
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

---

### Post by rsambuca on 2007-02-06
Try adding this line to your "Device" Section and restart
```
    Option 	   "UseEdidFreqs" "True"
```
Maybe the EDID info will sort itself out then.

---

### Post by rsambuca on 2007-02-06
Actually, also just try ```
sudo nvidia-settings
```
and see if you can manually change anything in the control panel.

---

### Post by naoise on 2007-02-06
Ok, so i edited something in my config according to the nvidia forums, and now i am back on the live cd trying to figure out how to fix it. I don't think we made a backup of config,and if we did, i dont know the command to fix it. And I CAN change things in the control panel.

---

### Post by naoise on 2007-02-06
bump!

So Its back to original AGAIN, and i still can't figure out what to do. I want it to be visible and fix the TV thing.

---

### Post by rsambuca on 2007-02-06
Sorry, I'm out of ideas here.  :confused:

---

