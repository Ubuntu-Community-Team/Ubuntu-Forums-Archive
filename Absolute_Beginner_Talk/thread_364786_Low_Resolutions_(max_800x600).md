---
title: "Low Resolutions (max 800x600)"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by RyanOmailley on 2007-02-18
I have just installed Ubuntu, and now that my networking troubles are cleared up (thanks, guys!) I am trying to figure out how to get my onboard graphics running.

It is an ATI Xpress 200, and as is my only screen resolutions are 640x480, or 800x600 (unsuitable!).

---

### Post by r4ik on 2007-02-18
Try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck!

---

### Post by RyanOmailley on 2007-02-18
I have tried that, however my max resolution is still 800x600 and max refresh rate is still 60Hz

---

### Post by The Noble on 2007-02-18
It sounds like you will either want the radeon or fglrx drivers for your card. Are you a gamer? Are you planning on using beryl or compiz any time soon? I really don't have a computer (under linux) that has an ati card, so I can't give you a step by step guide, but I at least know the basics. From what I have heard, the radeon driver will work great with your setup, and should support AIGLX form the get-go. Performance will be a problem some of the time with games, but everything should work well.

This thread:
[html]
http://www.linuxforums.org/forum/ubuntu-help/64489-ati-radeon-xpress-200-cant-change-screen-resolution.html
[/html]
 Should help if your read through it.

Edit:
I am incorrect in assuming that the radeon driver supports 3D for you card. The wiki states that it only has 2D support, so it is your choice to go with the closed source fglrx drivers or the open source radeon drivers.

Radeon Driver setup:
[html]
https://help.ubuntu.com/community/RadeonDriver
[/html]

FGLRX driver setup:
[html]
https://help.ubuntu.com/community/BinaryDriverHowto/ATI
[/html]

Goog luck.

---

### Post by RyanOmailley on 2007-02-18
Works great, thanks.

Although resizing windows seems to be exceptionally sluggish when compared to XP.

---

### Post by The Noble on 2007-02-18
What driver are you using? Try googling for that solution (or looking in these forums), as I almost guarantee that someone can answer that more elegantly than me.

---

