---
title: "Removing hardware"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by capnchicken on 2006-08-15
I have ubuntu server installed, just so I can play around with things. Do you have to do anything before you remove a piece of hardware?

Because I want to remove the video card on my box and just use the video on the motherboard so I can have a spare card. Will there be any problems, or should I edit some config files first?

---

### Post by capnchicken on 2006-08-18
I'm still not sure if there are still drivers hanging around that box for that card after the install or something, but I doubt it since I never ran X. I removed the video card, and everything seems to work, if there is something left over from before I'm too much of a noob to know where it is :) .

---

### Post by John.Michael.Kane on 2006-08-18
After you shutdown the machine,and have it set the way you want. you may have run ```
**[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]**
``` **Then select the resolution of the screen.**

---

