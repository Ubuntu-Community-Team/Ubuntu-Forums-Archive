---
title: "Log on Resolution Problems"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-09-04
Hello,
   I've looked for the right answer to this and haven't been able to find it yet....I just got a fresh install and installed my ATI drivers. But when I went to restart X it wouldn't show up on my monitor and said the it was out of range. So I control alt minus  it and lowered the resolution to something my monitor could handle. The problem is whenever I start X it wants to start in about 2100x1900 or something. But as soon as I log on it goes to 1680 by 1050 and I can once again see how I should..any answers?

---

### Post by jombeewoof on 2007-09-04
```
 sudo nano /etc/X11/xorg.conf 
```

scroll to the bottom of the file and you will see all of your available resolutions and color depths.
the first one is the default. If the default doesn't work, you can just delete it.

make sure you delete it from either all color depths, or at the very least your default color depth.(usually 24)

---

### Post by toasty_ghosty on 2007-09-04
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Prim$
        Monitor         "HW223"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1680x1050"     "1600x1200"     "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1680x1050"     "1600x1200"     "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1680x1050"     "1600x1200"     "1400x1050"    $
  EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1680x1050"     "1600x1200"     "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1680x1050"     "1600x1200"     "1400x1050"    $
        EndSubSection
        SubSection "Display"
                Depth   24
EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection



Is anything right there? Or wrong?

---

### Post by jombeewoof on 2007-09-04
looks good to me

---

### Post by toasty_ghosty on 2007-09-04
It still does it. I just tested it by resetting X.

---

### Post by VraiChevalier on 2007-09-04
Don't know if this will help or is even the same problem but I have had the situation where I could not set the correct screen resolution.

The fix was to enter the Horizsync and Vertrefresh rates in xorg.conf.

See this thread: [http://ubuntuforums.org/showthread.php?t=542491](http://ubuntuforums.org/showthread.php?t=542491)

---

### Post by toasty_ghosty on 2007-09-04
I had that problem earlier but I figured that out. It is only before I log on to my account.

---

### Post by jombeewoof on 2007-09-04
change the default depth from 24 to 16.
all instances of it.
you might also want to change 1600x1200 to 1680x1050

---

### Post by alienexplorers on 2007-09-04
If none of these fixes work you could try using a modeline in you monitor section of xorg.conf.  I use this and it forces the system to the set resolution and refresh rate.

---

### Post by toasty_ghosty on 2007-09-05
How would I come about doing that? Take this:

# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

and insert it where..

---

### Post by alienexplorers on 2007-09-05
open terminat and type gksudo gedit /etc/X11/xorg.conf.  Look for the monitor section as in the following example and enter it there.
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
    Modeline "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
    Option         "DPMS"
EndSection

---

### Post by LongJuanFeng on 2007-09-05
okay, this is the 3rd time I had to re-install ubuntu, I tried the sudo gedit method, the copy and paste method including the correct specs that were listed on a link for my graphics cards using sudo gedit, then finally the auto detection command in terminal. none work. everytime I restart, I'm given this stupid blue screen tellin' me my server x drive is wrong or something. can some one please provide a permanent solution to this woe?

---

### Post by alienexplorers on 2007-09-05
If you have a question then start your own thread.  Do not jump in to a thread that is already open.
> **LongJuanFeng said:**
> okay, this is the 3rd time I had to re-install ubuntu, I tried the sudo gedit method, the copy and paste method including the correct specs that were listed on a link for my graphics cards using sudo gedit, then finally the auto detection command in terminal. none work. everytime I restart, I'm given this stupid blue screen tellin' me my server x drive is wrong or something. can some one please provide a permanent solution to this woe?

---

### Post by toasty_ghosty on 2007-09-05
Where would I insert that modline?

---

### Post by alienexplorers on 2007-09-05
Read Post # 11 and you will see where to put it.  It goes in xorg.conf under the "MONITOR" section.

---

### Post by alienexplorers on 2007-09-06
i really love people who write questions and never come back to read them or let you know if what you told them worked or not.

---

### Post by toasty_ghosty on 2007-09-06
Actually I did fix it. I just hadn't been at my computer and been able to work on Ubuntu all day so don't think I wasn't courteous enough not to respond. I inserted the modeline and updated my drivers and it happen to fix the issue. So thank you.

---

### Post by alienexplorers on 2007-09-06
Your Welcome!!!!!!

---

