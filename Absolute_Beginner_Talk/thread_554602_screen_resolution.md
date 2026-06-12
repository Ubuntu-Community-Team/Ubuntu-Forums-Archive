---
title: "screen resolution"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by mr2v6 on 2007-09-19
Greetings,
I installed ubuntu on a dell dimension 5150 pc with a nvidia video card.
For some reason, the screen resolution is only 3 choices. And the highest one is 1024x768. 

Is there a way to have this adjusted to 1680x1050, without adjusting xorg or going to Gedit and adding this resolution.  (because it bombs on me - and end up reinstalling the software once again.)

Any help would be appreciated.

Thank you,
Raymond

---

### Post by mikeyphi on 2007-09-19
Have you enabled the Restricted Drivers?
System/Administration/Restricted Drivers Manager

---

### Post by mr2v6 on 2007-09-19
Hello,
Yes I was able to do this but it gave me resolution lower than 1024x768.

Raymond

---

### Post by Joeb454 on 2007-09-19
Have you tried using a different text editor to alter the xorg.conf file?

Other than that, I used Envy (search Google) to install the drivers for my Nvidia card

---

### Post by anemptygun on 2007-09-19
> **Joeb454 said:**
> Have you tried using a different text editor to alter the xorg.conf file?

Other than that, I used Envy (search Google) to install the drivers for my Nvidia card

I agree, try a different text editor. Sometimes you just have to do things the hard way.:-?

---

### Post by mr2v6 on 2007-09-21
It now worked for me, what was done was went to xorg conf, and changed the resolution (horizontal and vertical) respectively according to the monitor make and model,  and inserted the desired resolution.  Then save.

---

