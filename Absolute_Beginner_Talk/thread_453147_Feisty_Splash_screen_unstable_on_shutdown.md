---
title: "Feisty Splash screen unstable on shutdown"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by paddyboy on 2007-05-24

Hi (newbi),
Installed 7.04 yesterday on dual boot and all went well. Got synaptic updates, installed nvidia-glx and updated xorg.conf. Set background and screen saver etc. All great, no problems. 
However on shutdown the Ubuntu splash screen is VERY unstable. It is not centered on the screen but is way over to the right,causing it to wrap around to the left. So 'tu' on left 'Ubun' on right. The progress bar is working and it does shut down. But it jumps and shakes and whizzes past.

Is this symptomatic of something nasty going on under the hood ? Any ideas how to fix it ? Or should I just run away when I shut down :)

Running AMD sempron 3400+, Feisty -i386 (Kernel 2.6.20-15(generic), Graphics nvidia GeForce 6100 + nvidia-glx)

---

### Post by jonom on 2007-05-24
Sounds like the monitor is losing sync - like it's running at too-high of a frequency. Not sure how to fix it though.

---

### Post by paddyboy on 2007-05-25
Mmm, that's very interesting. I manually set the horizontal and vertical sync rates in my xorg.conf based on info I got from the notebook manufacturers website it set it thus :

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-85
        VertRefresh     50-120

Do these look too high to you ? Would reducing these do bad things ? What effects can getting these numbers wrong result in.?

Thanks

---

### Post by jonom on 2007-05-25
Not sure, but maybe using the Nvidia control panel to adjust your refresh rates might work better than hard-coding them.

But I'm just guessing.

---

