---
title: "monitor out of range - v710"
date: 2007-11-19
forum: Apple PPC Users
---

### Post by ubun942 on 2007-11-19
Hello:  I'm getting the "monitor out of range" message others have encountered.  This is on a G4 sawtooth.  The install only goes to the screen that gives instruction to hit the "enter" key or do some other brief commands first.  None of those work, the "out of range" message appears immediately, boot is terminated.  I did look at some answers that came up here, but they seem for intel/windows.  How have you fixed this?  The monitor is a wide screen 19 inch, in OS X.3.9 it's set for 1400x900.   For this I set it to 800x600 (640x480 didn't work), while in OS X, but this made no difference.  Thank you.

---

### Post by oswaldkelso on 2007-11-19
You probably need to find your monitor refresh rate to configure it. It will look some thing like this  71-73 for vertical and 70-140 horizontal.

Try installing with the graphic installer off

If your trying gutsy gibbon dont. There are alot of problems at the moment on ppc with it. Use an older version of ubuntu the alternative cd seem the best bet on older hardware.

If that fails you can try my debian net install  but you would still need your monitor information

make sure your firmware is upto date. [firmware link]("http://docs.info.apple.com/article.html?artnum=86117")

also see resetting your [p-ram]("http://docs.info.apple.com/article.html?artnum=2238")

My [Debian install how to]("http://www.my2bits.org/?p=76") its specifically for for imac/emac crts but should work for most macs if you know your monitor settings

---

### Post by Old_Grey_Wolf on 2007-11-21
I would suggest using the 7.04 alternate CD, try using the oem-powerpc option at the first prompt. It worked for me. Then I was able to install updates once Feisty 7.04 was installed.

---

