---
title: "Nvidia Problem with Edgy"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by npem on 2007-02-09
Hi, I installed the latest Beryl software, but now cannot start the XServer. Uninstalled Bery and moved the backup xorg.conf file back and restarted gdm, but the problem remains.

The error is:
(EE) No drivers available.

Fatal server error:
no screens found

My card is an FX5200

My xorg.conf file has the following:
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        128000
EndSection

Section "Monitor"
        Identifier      "Dell"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "Dell"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection


THis is very frustrating, so help would be very welcome,

Phil.

---

### Post by arochester on 2007-02-09
At the command line prompt input:
> sudo dpkg-reconfigure xserver-xorg
This will start a text based wizard. If you do not know the answer to any questions go with the suggested default answer. This should restore functionality.

To install Nvidia I found the script "Envy" very good. It checks which video card exists, downloads and installs the correct drivers for Nvidia or ATI. Read about it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by npem on 2007-02-09
Hi, I installed the latest Beryl software, but now cannot start the XServer. Uninstalled Bery and moved the backup xorg.conf file back and restarted gdm, but the problem remains.

The error is:
(EE) No drivers available.

Fatal server error:
no screens found

My card is an FX5200

My xorg.conf file has the following:
Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
Driver "nvidia"
BusID "PCI:1:0:0"
VideoRam 128000
EndSection

Section "Monitor"
Identifier "Dell"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
Monitor "Dell"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1280x800" "1200x800" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection


THis is very frustrating, so help would be very welcome,

Phil.

---

### Post by divague on 2007-02-09
How come you grahic card is a nvidia FX5200 and is recognized as a geforce 4 mx 4000??

Try reinstalling the nvidia drivers.

---

### Post by npem on 2007-02-09
THX for the info. I had used xserver-xorg, but envy has saved the day.

Now the resolution is poor, choces of 1024, 800 and 640, but my xorg.conf file is:

 Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "Dell"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes            "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Before I had the problem with Beryl and the hraphics device, I had a higher resolution available.

Any Ideas?

Phil.

---

### Post by npem on 2007-02-09
THX, I (apologies) posted this initailly in the Absolute Beginner Talk and now have it working (except the resolution is too low)

In answer to the question. I had problems when I installed dapper and a look arounf the forums showed a listing for xorg.conf with this config for a 5200, tried it and it worked, so it has remained ever since.

---

### Post by RomeReactor on 2007-02-09
Hi. Perhaps Beryl messed up your nVidia drivers. 

**1.-** From the command line write

```
sudo nano /etc/X11/xorg.conf
```

and on the "Device" section change the driver back to "nv". Save and restart. If that doesn't bring back X, go to **step 2**; If it does, then search Synaptic for your drivers and see if they're still installed. If they are, then press **CTRL+ALT+F1** to get you to the command line, and

```
sudo /etc/init.d/gdm stop
```

to stop the gnome display manager. 

**2.-** Then use nano again to revert to the "nvidia" drivers, and

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and after that

```
sudo /etc/init.d/gdm start
```

If that doesn't get you to your desktop, press **CTRL+ALT+F7** (or **sudo reboot**)

**EDIT: Gahhh, to slowwww... started answering when i saw the 3rd post...**

---

