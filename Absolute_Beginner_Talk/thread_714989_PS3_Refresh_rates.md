---
title: "PS3 Refresh rates"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by JazzUK on 2008-03-04
I was wondering whether someone could help me with my PS3. How can I increase my refresh rate from 30Hz to 60Hz? It strains my eyes really bad in this mode and my eyes are crap anyway. :confused:
It's running in 1080i if that helps. Or how about the NVidia Restricted Drivers? Is there a way to put them on the PS3 properly?

I know about ''sudo dpkg-reconfigure xserver-xorg'' but it never works :(

HALP a n00b please???

---

### Post by Origin415 on 2008-03-04
You can try editing your xorg.conf.

Go to your terminal and type

```
sudo nano /etc/X11/xorg.conf
```

Go down to the moniter section, and there should be a bunch of lines like 
ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync

the @# is the refresh rate, change that.


BTW, Ubuntu is definitely not the best operating system to run in your situation, its kernel probably doesnt support it very well, especially the Cell processor. Heck, I'm not sure how you got it to run -- Ubuntu doesnt have a PPC64 edition, the closest architecture to Cell. Gentoo has a specific Cell kernel, you could try looking into that, you will get a huge performance boost if you can properly handle the 8 SPUs.

---

### Post by JazzUK on 2008-03-05
Thanks. I'll give Gentoo a try

---

