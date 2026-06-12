---
title: "Black screen, none responsive system."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Lutherlee on 2007-08-01
My system;
AMD 64 4000+ (AM2)
ASUS M2NPV-VM
Nvidia 8600GT 
2g Corsair memory
Seagate 250g HD

Dual booting Ubuntu 7.04 with XP, partitioned free space on HD via XP Disk Management.  Intalled Ubuntu, while booting to the liveCD i did experience the black screen and some system inactivity, but this did not deter the initial install, reboot and upgrade.  Now while logging into Ubuntu the system stops responding.

While still able to access the OS I was unable to adjust the screen resolution, I mention this considering the chance of graphical error.

Any suggestions?

---

### Post by apswartz on 2007-08-01
print the contents of your /var/log/Xorg.0.log file here (or the relevant portions)

---

### Post by Lutherlee on 2007-08-01
How could I find that informations if I am unable to boot into Ubuntu?:confused:

---

### Post by apswartz on 2007-08-01
Sorry, you said you couldn't login to Ubuntu - I took that to mean you got as far as the login screen.

---

### Post by Lutherlee on 2007-08-01
Meaning I get to the boot manager, my fault for not being more specific, then the system stops.

---

### Post by confused57 on 2007-08-01
> **Lutherlee said:**
> Meaning I get to the boot manager, my fault for not being more specific, then the system stops.
If you can boot into Recovery mode, you could try:
```
dpkg-reconfigure xserver-xorg
```
Select "no" on the first screen to automatically configure your xserver, then you can go with the defaults for everything else...except when you get to the video driver, choose "vesa"...when you're finished, press "Esc".  This "should" get you to a login screen.  If this works, it will let you know it is a video driver issue, then all you would need to do is install restricted drivers for your card.

---

### Post by Lutherlee on 2007-08-01
Thanks, that worked I'm now posting from back under Ubuntu.

Further questions would be which drivers for the video should I now install, and would that resolve another issue with only being able to run my screen resolution at 1024x768?

Thanks again for this assistance.:KS

Also of  note, I'm pulling much information from the link "Ubuntu Tutorials", thanks for those links.

---

### Post by confused57 on 2007-08-01
> **Lutherlee said:**
> Thanks, that worked I'm now posting from back under Ubuntu.

Further questions would be which drivers for the video should I now install, and would that resolve another issue with only being able to run my screen resolution at 1024x768?

Thanks again for this assistance.:KS

Also of  note, I'm pulling much information from the link "Ubuntu Tutorials", thanks for those links.

Glad to have helped & that the vesa driver enabled you to get to a GUI.  You can try installing a proprietary nvidia driver for your card:

First make a backup of your working xorg.conf:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
```

You might want to read through the instructions given by bodhi.zazen in this thread for installing Nvidia drivers from the Nvidia website:
[http://ubuntuforums.org/showthread.php?t=495464&highlight=June+21](http://ubuntuforums.org/showthread.php?t=495464&highlight=June+21)

I'm not sure, but the automated Envy installer may be able to install the driver you need:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

You can get Envy here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You might want to try Envy first to see if it recognizes your video card...if you install the Nvidia drivers and get an xserver error when you boot into Ubuntu...press "Ctrl+Alt+F1" to get to a console, login, enter:
```
sudo /etc/init.d/gdm stop
cd /etc/X11
sudo cp xorg.conf_backup xorg.conf
```
this will restore your working xorg.conf with the "vesa" driver

Then enter:
```
startx
```
or if  startx doesn't work:
```
sudo /etc/init.d/gdm start
```

If the Nvidia driver installs & works correctly, you shouldn't have any problem selecting the resolution(s) that you want.

---

### Post by Lutherlee on 2007-08-02
Envy worked installing the latest Nvidia drivers, but I'm still unable to raise my screen resolution any higher than 1024X768.

I'll play around more with this in the am, slumber calls....

Thanks very much for the help.

---

### Post by confused57 on 2007-08-02
> **Lutherlee said:**
> Envy worked installing the latest Nvidia drivers, but I'm still unable to raise my screen resolution any higher than 1024X768.

I'll play around more with this in the am, slumber calls....

Thanks very much for the help.

Excellent information in this thread, pay particular attention to the replies & advice given by tseliot:
[http://ubuntuforums.org/showthread.php?t=432056&highlight=xorg.conf](http://ubuntuforums.org/showthread.php?t=432056&highlight=xorg.conf)

You might also want to create a 2nd backup of your xorg.conf with the nvidia drivers:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_baknvidia
```

This way you'll have a backup with the vesa driver(xorg.conf_backup) and the nvidia driver(xorg.conf_baknvidia).

You might be able to manually add the resolutions you need to your xorg.conf...near the bottom of your xorg.conf file you'll see default color depth is set to 24, you should be able to add any resolutions to the Mode line 24...
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Lutherlee on 2007-08-02
Here is a copy of my xorg-conf file.

Section "Monitor"
    Identifier     "Generic Monitor"
    DisplaySize     342    271
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card Nvidia 8800"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card Nvidia 8800"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1440" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Though "1920x1440" is listed here, I am unable to choose that resolution from "screen resolution".

---

### Post by Lutherlee on 2007-08-02
Final note, I was looking around under "Applications>System Tools>Nvidia Tools" and found the screen resolution setting that allowed me to adjust the screen to my desired resolution.

Previously I was looking under "System>Preferences>Screen Resolution" which I was not able to adjust my resolutions.

Thanks for all the help.:guitar:

---

### Post by confused57 on 2007-08-02
> **Lutherlee said:**
> Final note, I was looking around under "Applications>System Tools>Nvidia Tools" and found the screen resolution setting that allowed me to adjust the screen to my desired resolution.

Previously I was looking under "System>Preferences>Screen Resolution" which I was not able to adjust my resolutions.

Thanks for all the help.:guitar:

No problem, glad everything worked out...good job on your part getting your system configured correctly.

---

