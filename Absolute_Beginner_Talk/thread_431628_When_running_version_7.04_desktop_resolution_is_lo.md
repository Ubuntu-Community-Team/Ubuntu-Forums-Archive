---
title: "When running version 7.04 desktop resolution is low"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by waynepr72 on 2007-05-03
Hi,

I have just loaded the live CD of the latest release and find that my highest resolution is 1024 x 768, I have a 19 inch monitor and the previous version of Ubuntu 6.01 ran automatically at 1280 x 1024 perfectly.  It is on a ATI Radion 256mb 9200 graphics card. Anyone know how to resolve this on the 7.04 version?

Thanks in advance,

Wayne

---

### Post by starcraft.man on 2007-05-03
ummm, you probably only need to redetect your monitor, I wouldn't worry about it.

Open the terminal and type:

```
sudo dpkg-reconfigure xserver-xorg
```

Should fix it, just say ok through everything, when you get to the resolution selection, make sure 1280 X 1024 is selected and any other lower resolution you wanna be able to switch to.

---

### Post by lamalex on 2007-05-03
edit your xorg.conf
```

sudo nano /etc/X11/xorg.conf

```
and add the desired resolution. you'll see where, it looks like this...
> Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x800"
        EndSubSection
EndSection

that's a copy of mine, you would want to add your 1280 x 1024 before each 1280x800, then restart x (control alt backspace) and you should then be able to reset it using the screen resolution tool  in preferences

---

