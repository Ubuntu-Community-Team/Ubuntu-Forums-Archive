---
title: "Refresh problems."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by whiteguysamurai on 2007-06-19
I have fixed my problem of getting it to go to 1600x1200, however i still can't get it past 60hz

I'm going to post my xorg here in hopes someone can fix of show me what i did wrong.

Thanks.```
ection "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-75
        Vertrefresh     50-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON 9800"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1600x1200_85"  "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1600x1200_85"  "1440x900"      "1400x1050"    $
        EndSubSection

```

---

### Post by Clay_Banger on 2007-06-19
> **whiteguysamurai said:**
> I have fixed my problem of getting it to go to 1600x1200, however i still can't get it past 60hz

I'm going to post my xorg here in hopes someone can fix of show me what i did wrong.

Thanks.```
ection "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-75
        Vertrefresh     50-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON 9800"
        Monitor         "Generic Monitor"
        Defaultdepth    24
  [B]      SubSection "Display"
                Depth   1
                Modes           "1600x1200_85"  "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1600x1200"     "1440x900"      "1400x1050"    $
        EndSubSection[/B]
        SubSection "Display"
                Depth   24
                Modes           "1600x1200_85" ** "1440x900"      "1400x1050"    $**
        EndSubSection

```

Backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
and remove everything i have highlighted in bold above, and change "1600x1200_85" to "1600x1200@85"

---

### Post by whiteguysamurai on 2007-06-20
Thanks.
I'm sure that would work too.
I fixed it last night by reconfiguring xorg and telling it i have a 21" monitor.
Now it's time to see if I'm brave enough to hose my install and try installing beryl.

Thanks again for the reply!

---

### Post by whiteguysamurai on 2007-07-06
Just an update.

Reconfiguring the xserver fixed this.

---

