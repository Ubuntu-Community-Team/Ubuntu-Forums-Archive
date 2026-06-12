---
title: "1680x1050 problem driving me crazy!"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by opiv421 on 2007-05-10
I just did my first ever linux install this morning (Feisty Fawn) and all night I've been trying to get my Syncmaster225bw monitor recognized at 1680x1050. Currently the max resolution recognized is 1280x1024 @ 57Hz. I've been trying to configure the xorg.conf file for a few hours now and haven't had any success. Below is my xorg.conf file. Any help would really be appreciated. Thanks.

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-64
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7900 GS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768" "832x624" "800x600" "720x400" "640x480" $
        EndSubSection

        SubSection "Display"
                Depth   4
 Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768" "832x624" "800x600" "720x400" "640x480" $
        EndSubSection

        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768" "832x624" "800x600" "720x400" "640x480" $
        EndSubSection

        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768" "832x624" "800x600" "720x400" "640x480" $
EndSubSection

        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1280x960"      "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"       "640x480"   $
        EndSubSection

        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1280x960"      "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"       "640x480"   $
        EndSubSection

---

### Post by bobplano on 2007-05-10
you could always try
```
sudo dpkg-reconfigure xserver-xorg
```
you could also try adding 1680x1050 into the 24 bit depth section

---

### Post by sloggerkhan on 2007-05-11
Have tried adding "1680x1050" on the Modes line?

---

### Post by Rotaj on 2007-05-11
Did you let the ubuntu install the drivers? If so, you might like to let [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") do the nvidia driver install. also check under System\admin\restricted drivers

---

### Post by opiv421 on 2007-05-11
I ran envy and rebooted and the xorg file crashed on boot! >.< I'm running off the cd now trying to figure out how to restore the xorg file. :(

---

### Post by mrmonday on 2007-05-11
Try:

```
sudo envy -t
```

If you can get to a CLI. If not do it in recovery mode. Uninstall the drivers, and get envy to reconfigure your xorg. Hopefully you will now be able to get into a GUI.

---

