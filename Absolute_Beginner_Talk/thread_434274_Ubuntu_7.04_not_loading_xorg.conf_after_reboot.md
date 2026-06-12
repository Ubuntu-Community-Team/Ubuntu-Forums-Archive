---
title: "Ubuntu 7.04 not loading xorg.conf after reboot"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by cheshiredragon on 2007-05-05
About a month or two ago I D/Led and installed Ubuntu 6.10.  Installed Automatix had it install my video card and then I installed Beryl.  Worked great.
The one problem I had and I thought it was because of the video driver I had I was not able to use dual monitors.  I accepted that and everything was good.  When I loaded Ubuntu it did use two screens until it came to the login screen and the secondary monitor just turned off and went into standby mode.
Now, ver 7.04 is out so, I installed that today and strangely enough it wanted to use my secondary monitor as the primary.  OK, after I get the drivers installed I can change that and I did.  I was also able to use dual monitor setup.  Now my problem is that I can't save the configuration to the xorg.conf file.  I used the command "gksudo nvidia-settings" in terminal for admin rights to SAVE the file.  It worked and I verified that it worked.  After reboot, though, it reverts back to the original setting of my secondary monitor as the primary.  So I go back to check the xorg.conf file and it is still the changed and verified file its just that Ubuntu doesn't want to use it.
The video card in question is a GeForce FX 5200 128MB
The ONLY thing I can think of why it is doing this is the video driver.  in teh new 7.04 Automatix installed the 9755 driver and in 6.10 it installed the 8778?(I think) driver.  I decided to test my theory on this  so I ran the live CD of 6.10 and it did the same thing as 7.04 which has never happened before.  I have no idea what is going on.  IF I can get that xorg.conf file to reload after reboot all should be fine.

Any help is much appreciated.

---

### Post by ronocdh on 2007-05-05
Have you tried just editing the xorg.conf by hand? You could use ```
sudo gedit /etc/X11/xorg.conf
```Change the command as appropriate for you (if you like to use nano, for instance, etc.). Post back with results.

---

### Post by cheshiredragon on 2007-05-06
YAY!!!  It worked...weird, I could manually edit it with the other command I used but, it just didn't reload it after reboot.

The only thing that bugs me now is that the it puts the login screen on the secondary monitor, but I can live with that.  At least it works now :)
Thank You very much!

---

### Post by Nythain on 2007-05-06
i have that exactly same card... try either switching the vga inputs, and or post your xorg.conf and maybe i can help you get it goin right... it all works fine on my end, feisty with nvidia-glx-new (the 7552 driver) and the gforce fx5200... so all id really have to do is compare your xorg.conf with mine for any major differences

---

### Post by cheshiredragon on 2007-05-06
I was thinking about switching the ports, but I dual boot with Windows and it would throw windows off.  I decided to scrap the who dual monitors under Ubuntu a few min ago and I reedited the xorg.conf file and everything is good , but now for some reason Ubuntu refuses to load my primary monitor res at 1280x1024 and puts it at 1024x768.  Both comands from about don't seem to help and I even set it so that the 1280x1024 is the only res in xorg.conf.  I can go into the nvidia manager and change it and it changes , but if I CTRL+ALT+BACKSPC it loads the login screen at 1280x1024, but as soon as it hits the Gnome desktop, back to 1024x768 it goes.

---

### Post by alienexplorers on 2007-05-06
When you run NVIDIA Manager are you running it in SU mode 

> gksudo nvidia-settings

When you set the screen to 1280x1024 click on save to X configuration file, it will then keep the settings.

---

### Post by cheshiredragon on 2007-05-06
yes, I do use "gksudo nvidia-settings" and I have also tried "sudo gedit /etc/X11/xorg.conf"
The latter worked great to get the dual monitors up and running where it did hold the res for both monitors, but now for some reason when I reverted back to a single monitor it doesn't want to keep the res up at 1280x1024 and puts it down to 1024x768.

---

### Post by alienexplorers on 2007-05-06
> Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024_65 +0+0; 800x600 +0+0; 640x480 +0+0; 1280x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Does your xorg.conf have a metmodes line.  Mine orginally did not and once It was added it my screen resolution problams went away.  Mine was doing the same as yours.  Also, I had to add a modeline and UseEDID "False" (see below)

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Delta"
    ModelName      "Delta DE-570 BA"
    HorizSync       30.0 - 70.0
    VertRefresh     60.0 - 120.0
    Option         "UseEDID" "FALSE"
    Option         "IgnoreEDID" "TRUE"
    Modeline       "1280x1024_65.00"  119.40  1280 1368 1504 1728  1024 1025 1028 1063 -HSync +Vsync
    Option         "DPMS"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

---

### Post by cheshiredragon on 2007-05-06
This is my xorg.conf file.....as you can see the only thing I changed was modes by giving it ONLY the chance to load at 1280x1024 and that doesn't seem to work.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Envision EN9410e"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT-1: 1280x1024_75 +0+0; CRT-1: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection
```

---

### Post by alienexplorers on 2007-05-06
Looks like it should work.  You got me on this one.

---

### Post by cheshiredragon on 2007-05-06
I think I figured out what I did.  I moved my comp into my room for an evening and hooked it up to just one monitor then when I put it back out in the living room I reconnected it to the two monitors backward which switched them around, but since windows was using just the one monitor it goofed the config.  Long story short - > try either switching the vga inputs
yeah, I did that and I am going to reinstall Ubuntu cause it is really screwed up now.
Thank you all for your help :)

---

