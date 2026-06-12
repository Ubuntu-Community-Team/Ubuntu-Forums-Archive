---
title: "Screen flickers after changing the screen resolution"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by henrypradeep on 2007-12-14
Hi i have selected  the Screens resolution 1280 x 1024  using sudo dpkg-reconfigure xserver-xorg. But once i select this resolution, my screen is getting flickered. 

Should i need to change anything to work???

My /etc/X11/xorg.conf reads like this.


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by siciliancasanova on 2007-12-14
Is your refresh rate correct for that monitor?  Search your monitor on google or look in the manual and it should give you the refresh rate.

---

### Post by henrypradeep on 2007-12-14
Display

Diagonal Size: 17"

Viewable Size: 16"

Dot Pitch / Pixel Pitch: 0.24 mm

Max Resolution: 1280 x 1024 / 60 Hz

Max Sync Rate (V x H): 160 Hz x 70 kHz

Video Bandwidth: 110 MHz

Controls / Adjustments: Brightness, contrast, H/V moire, H/V position, H/V size, trapezoid, degauss, parallelogram, pincushion

Signal Input: VGA



So where i am supposed to change this resolution... My current Refresh rate is 85 Hz....

---

### Post by siciliancasanova on 2007-12-14
Well I think that's your problem then if it's running at 85 and the specs only say it can run at 60.  What's odd is that it's even displaying anything.

What's odd is that these numbers seem to low for 85hz, someone correct me if I'm wrong...

```

HorizSync 28-64
VertRefresh 43-60

```

---

