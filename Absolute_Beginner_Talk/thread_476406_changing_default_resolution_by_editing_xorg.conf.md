---
title: "changing default resolution by editing xorg.conf"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by rajan on 2007-06-17
Hi, I bought a computer for a relative and of course i put ubuntu on it. I'm having two problems. One is that I cannot get the screen resolution to boot to the default that I've set it to using the GUI (from the top toolbar thingy under "preferences"). Every time I reboot it returns to a resolution that the monitor can't handle. I installed ubuntu on the box while the box was connected to a different monitor and now it thinks that it can use a resolution setting that's much larger than the monitor can handle. 

I can open the xorg.conf file using emacs, but i can't figure out which part codes for the default monitor resolution. 

The second problem I'm having is that I can't find a dial-up utility for linux. Does anyone have any ideas? 


Thanks,

rajan

---

### Post by Happy_Man on 2007-06-17
Are you using a Nvidia card? If so, open a terminal (Applications --> Accessories --> Terminal) and type:
```
sudo nvidia-settings
``` Change your default resolution in there, and then click "save to xorg.conf file" to write the changes. Now your computer should be OK betweeen boots. 

If you're not using Nvidia, post back with what kind of card you're using.

---

### Post by HereInOz on 2007-06-17
You could open a terminal and enter:

sudo dpkg-reconfigure xserver-xorg

This will run you through a utility which will allow you to configure your xserver, and at one point, there will be a place where you can select the screen resolutions which you wish to use.  Make sure that you only select the ones you want, and it should all come together.

---

### Post by Bruce Couper on 2007-06-17
> **Happy_Man said:**
> Are you using a Nvidia card? If so, open a terminal (Applications --> Accessories --> Terminal) and type:
```
sudo nvidia-settings
``` Change your default resolution in there, and then click "save to xorg.conf file" to write the changes. Now your computer should be OK betweeen boots. 

If you're not using Nvidia, post back with what kind of card you're using.

Hi Happy_Man

Thank you for this.  I was finally able to change the refresh to 85@1024x768 on my wife's SyncMaster 753DF.  However, I cannot get this to persist -- after restart it returns to approximately 60 Hz.  Also, the available resolutions under **System->Preferences-> Screen Resolution** show only the following at that resolution:


52, 57, 63, 64

I did choose Apply and I did save the settings.  The resolution did change in real-time.  So, I would greatly appreciate any guidance in this.  I'm clearly missing something.

Regards -- Bruce Couper

Relevant section of xorg.conf:

> Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster" 
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0" 
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1024x768 +0+0; 1024x768_85 +0+0; 1280x1024 +0+0; 832x624 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0; 1024x768_70 +0+0" 
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by w4ett on 2007-06-17
try this section in your xorg.conf:

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "metamodes" 1024x768_85 +0+0; 1280x1024 +0+0; 832x624 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0; 1024x768_70 +0+0"
SubSection "Display"
Depth 24
Modes  "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by meborc on 2007-06-17
in other words, delete the resolutions that you don't use from the file... save... reboot X (ctrl+alt+backspace)

or

when running sudo dpkg-reconfigure xserver-xorg be sure the choose the medium way to detect your monitor (or similar) so you can choose the default resolution/sync rate

---

### Post by w4ett on 2007-06-17
> **meborc said:**
> in other words, delete the resolutions that you don't use from the file... save... reboot X (ctrl+alt+backspace)

or

when running sudo dpkg-reconfigure xserver-xorg be sure the choose the medium way to detect your monitor (or similar) so you can choose the default resolution/sync rate

Thanks meborc....I'm not quite awake yet....just having my first cup of coffee...(I SHOULD HAVE EXPLAINED) what I did to the file....Sorry :)

---

### Post by rajan on 2007-06-17
thanks for the help everyone. i'll be checking up on it soon. i would have used the dpkg route, but i can't connect to the internet yet. 

as for the dialup question, i found this thread:
[http://ubuntuforums.org/showthread.php?t=475783](http://ubuntuforums.org/showthread.php?t=475783)

---

