---
title: "I can't get Linux to a high res"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Emarian on 2007-09-01
For some reason, Linux won't go to a high res..It's stuck at 640 x 480...SUPER zoomed in. >.> I tried raising it, but that's the highest it will let me go. Windows XP can go up to 1600 x 1200...Why can't Linux? Is there a way to get this working right?

EDIT:
I have an eMachines T3124..Nvidia 6600 chipset. Full specs can be found here (Right click the plus sign next to specifications):
[http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3124](http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3124)

---

### Post by Kingsley on 2007-09-01
Try ```
sudo dpkg-reconfigure xserver-xorg
```
Keep pressing enter until it starts asking questions about your monitor. Then choose the correct resolution sizes.

---

### Post by ramjet_1953 on 2007-09-01
What video card / video chipset do you have?

You may need to install a driver for your video to work properly.

Check out this link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)

Regards,
Roger 8-)

---

### Post by nonewmsgs on 2007-09-01
try envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Emarian on 2007-09-02
Wow, thanks for the help guys. =P Anyways, I'll try envy, if that doesn't work, I'll read the docs, if that doesn't work, I'll do what the first reply said. It looks like some sort of command, like for the win command prompt. >.> Lol, I'm new to Linux. What should I enter that in? I'm good at windows, pff at Linux.

---

### Post by MenZa on 2007-09-02
> **Emarian said:**
> Wow, thanks for the help guys. =P Anyways, I'll try envy, if that doesn't work, I'll read the docs, if that doesn't work, I'll do what the first reply said. It looks like some sort of command, like for the win command prompt. >.> Lol, I'm new to Linux. What should I enter that in? I'm good at windows, pff at Linux.

Indeed. Lots of stuff in Linux is much easier and faster to do in the terminal in their GUI-equivalent programs, and you'll have to get accustomed to the terminal. It scares a lot of new users, but once you've learnt how to use it, you'll appreciate how powerful it is.

You could also do System -> Administration -> Restricted Drivers Manager and tick your driver in there. It should work a treat. :)

---

