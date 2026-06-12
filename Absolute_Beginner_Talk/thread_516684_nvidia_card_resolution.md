---
title: "nvidia card resolution"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by tumble on 2007-08-03
Hi, I've recently installed Ubuntu 7.04 on my pc (AMD 64 X2) dual booting with XP pro. I have a Nvidia 8800gts. I installed the Nvidia glx driver through the add/remove part I think its called. The problem is I cant change resolution higher than 1024/768 - I see its not using the driver but some other one. I tried to enable it but it doesn't seem to work. A fix would be usefull so I can play games and stuff too.  Can help would be great.

Tumble

---

### Post by Steve1961 on 2007-08-03
Type the following in a terminal:

sudo gedit /etc/X11/xorg.conf

Look for this section:

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
.....

If your xorg.conf just says nv rather than nvidia, change it to nvidia.  Then look at this section:


Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


and make sure the resolution you want is listed.  Then restart x (ctrl-backspace)

---

### Post by Hospadar on 2007-08-03
you can use ```
sudo dpkg-reconfigure xserver-xorg
``` to enable extra resolutions, as well as enabling the nvidia driver.  on the first page of the dialog, choose the "nvidia" driver instead of the "nv" driver.  then restart your xserver with ctrl-alt-backspace or by going to a text terminal with ctrl-alt-F1 and doing ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm stop
```
or ```
sudo /etc/init.d/gdm restart
```
these all do the same thing (restart your x server).

if x crashes and does not start up, do ctrl-alt-F1 and stop the x server with ```
sudo /etc/init.d/gdm stop
``` then I would use envy to find and install the proper driver.  from this text terminal, do ```
sudo apt-get install envy
envy -t
``` then remove and clean the nvidia installation with envy, but don't let it restart the x server yet, then use envy to find and install the proper driver, allow envy to edit your xorg.conf file and restart your x server at this point.  this should work.  

if it does not, use envy again to remove and clean your driver installation, then set your driver back to "nv" and restart your x server then go to the nvidia website, download their driver, go back to the text terminal, stop the x server, cd to where you saved the nvidia driver (probably ~/Desktop) ```
cd ~/Desktop
``` and do ```
sudo sh <the filename of name of the nvidia driver>
```  allow the installer to edit your xorg.conf file.

Hope this works!

---

