---
title: "Video Card Problem for the Experts"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-05-06
Just wondering if anybody can explain this to me, unless I have a defective video card (although it seems to work perfectly anywhere else.)  I tried installing Kubuntu 7.04 on a PC that had a EVGA Nvidia 6800 GS, and when booting from the LiveCD, the display only comes up as a garbled screen at the desktop (splash screen worked fine.)  I replaced it with a BFG Nvidia 7600 GT, and it works just fine.  Since getting it installed, I haven't tried switching the cards back.  Any ideas before I do that and possibly break Kubuntu (temporarily)?:)

---

### Post by taurus on 2007-05-06
You probably just have to reconfigure X again after you switch the graphic card.  Shouldn't be too hard to do.  

Boot into recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by therandman on 2007-05-06
Thanks Taurus!

---

### Post by Bachstelze on 2007-05-06
Have you tried usng an Alternate CD ?

Oh, never mind, I though you were stil stuck on the install. Taurus' advice might work, try that first :)

---

