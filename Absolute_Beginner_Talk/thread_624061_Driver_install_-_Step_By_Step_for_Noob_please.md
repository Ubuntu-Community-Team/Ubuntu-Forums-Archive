---
title: "Driver install - Step By Step for Noob please"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by oldguysrule on 2007-11-26
Please hold the laughter until the end

I've been using Ubuntu for a couple of months. Did have 'Feisty' installed and upgraded to 'Gutsy AMD64'.  I began having the random lockup/ freezes that other have been experiencing. I checked the 64 bit forum and found that people who installed the new beta nvidia driver were not having this problem anymore. So hitching up my britches I read some how too's - including the nvidia site how too and thought I'd take a shot at installing the newest driver. I downloaded the same and ran the .sh script but kept getting told X was still running. After much fumbling - still not sure how I did it (i think it was the innit 3 command???) I  managed to get the new driver installed. I rebooted the system and horror of horrors the only resolution I could get was 800x600 (native resolution is 1440x900) - tried a lot of things including sudo dpkg-reconfigure xserver-xorg. Filled in the appropriate information - but still only got 800x600. Went into /etc/X11 located xorg.conf and edited it - still no luck. I did notice a file in there xorg.safe but since xorg.conf was there I didn't think much about it. 
To make a long story short I finally just did a clean install. checked /etc/X11 and saw that lovely xorg.conf by itself.  I then enabled the restricted drivers. On reboot the only screen resolution was 800x600. Somewhat perturbed I checked /etc/X11 and saw that xorg.safe was back. I removed it - rebooted and everything was fine 1440x900 again. 
Sorry to be so long winded but I have 2 questions:
1) Why did the safe file show up?
2) Can someone tell me the proper way to stop X and install the nvidia drivers (so a noob would understand please).

Thanks
You can chuckle to yourself now!!!

AMD Athalon 64 X2 - 2.6GHz, 4Gb Ram, Dual boot Ubuntu and Vista
nVidia 6150SE on board graphic chip - 128Mb dedicated.

---

### Post by Hospadar on 2007-11-26
well!

Good news, you can probably fix it, bad news, you mucked it up with your install =P
First off, we need to be sure you are in fact using the drivers that you installed, could you do a "cat /etc/X11/xorg.conf" and copy the output.

Also, when you boot up, does it start up cleanly and just not give you extra resolutions, or does it give you an error message of some sort.

Also, while in gnome, could you tell us what happens when you type glxgears in a terminal?

What I think you will probably end up having to do, is using synaptic, uninstall "nvidia-glx" (or nvidia-glx-new depending on which one you have) then use envy to clean out the drivers you installed from the nvidia download, then reinstall with the nvidia download.  Grab the .deb from [this]("http://albertomilone.com/nvidia_scripts1.html") website, install it.  then go to a text terminal (ctrl-alt-F1) and run ```
sudo envy -t
``` use the options here to remove and clean nvidia drivers, then once that is done, run the nvidia download.  See below for stopping and starting X.

As for stopping and starting your X server, the proper way to do it is from a text terminal (ctrl-alt-F1) use any one of these three commands (use the one you need)```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart
```

---

### Post by oldguysrule on 2007-11-27
Thanks for the help Hospadar

Here are the results of cat /ext/X11/xorg.con - I did have to correct  the Horizontal Sync and Vertical Refresh rates as my monitor was not picked up correctly

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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "generic videocard"
        Driver          "nvidia"
        Busid           "PCI:0:13:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic monitor"
        Option          "DPMS"
        Horizsync       30-81
        Vertrefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "generic videocard"
        Monitor         "generic monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

When I boot there are no error messages and Ubuntu starts cleanly after the nVidia splash screen.   After I corrected the Horizsync and Vertrefresh rates all the extra resolutions were there.

Glxgears shows the gears and frame rates averaging 2039 FPS

Hope this helps

I did check the Envy site but Alberto's blog indicates the nvidia beta drivers are not included in the current release. As those are the drivers that seem to solve the lock up problem I guess I'd just better wait until either Envy or the repositories get those drivers. I still don't know why the .safe file showed up.
Thanks again

---

