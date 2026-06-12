---
title: "setting up monitor"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by windozer on 2007-03-06
I'm following a tutorial from somewhere trying to set up my monitor. 
It says:
"Adding custom modeline

Now, if you know what your monitor can do, for example 1024x768@75Hz (edit: choose decent resolution / refreshrate), you can open another terminal window (keep xorg.conf open in gedit) and enter:



Code:

 gtf horizontalresolution verticalresolution refreshrate

for example:

gtf 1024 768 75

Copy paste the output to your Monitor section."


So the monitor part in xorg.conf should look like this:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-61
        VertRefresh     50-120
  # 1024x768 @ 72.00 Hz (GTF) hsync: 57.67 kHz; pclk: 78.43 MHz
  Modeline "1024x768_72.00"  78.43  1024 1080 1192 1360  768 769 772 801  -HSync +Vsync
EndSection

Is that right? And also, does pressing ctrl+o save xorg.conf?

---

### Post by strikeback03 on 2007-03-06
Here is the section of my xorg.conf  that works.
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       48.0-75.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
    Modeline "1920x1200" 204.95 1920 2024 2272 2744 1200 1200 1203 1244
EndSection
```

the refresh is not enclosed in the ""

as for how to save, what editor are you using?

---

### Post by windozer on 2007-03-06
Well it said to open the file like this:
sudo nano /etc/X11/xorg.conf
So nano is the editor? It says ^O WriteOut at the bottom of the window. WriteOut means save?

What I need to know is, is this pasted in the right place?
# 1024x768 @ 72.00 Hz (GTF) hsync: 57.67 kHz; pclk: 78.43 MHz
Modeline "1024x768_72.00" 78.43 1024 1080 1192 1360 768 769 772 801 -HSync +Vsync

---

### Post by strikeback03 on 2007-03-06
in nano you use ctrl+x (Exit) to save - it will ask if you want to save before exiting the file.

here is the page I followed to install:  [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

I used this to generate my modeline: [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

as I said, yours does not look like mine, but I've only been using this for a week or so and I don't know if what you have will work or not.

---

### Post by maniacmusician on 2007-03-06
> **strikeback03 said:**
> in nano you use ctrl+x (Exit) to save - it will ask if you want to save before exiting the file.

here is the page I followed to install:  [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

I used this to generate my modeline: [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

as I said, yours does not look like mine, but I've only been using this for a week or so and I don't know if what you have will work or not.
including the refresh rate in the quotes works as well. However, it's possible it could be conflicting with the refresh rate outside the quotes, so you can try removing it to see what happens.

As strikeback03 said, in nano, you press ctrl + x, and it asks you if you want to save. you hit "y" for "yes". then, you have to restart the X server (ctrl + alt + backspace). **Warning: This will take you back to the login screen. Make sure you save anything you have open, or you'll loose whatever changes you've made since your last save**

---

