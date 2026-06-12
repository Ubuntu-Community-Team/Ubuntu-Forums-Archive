---
title: "dell e1505 intel 945gm &quot;No Screens Found&quot;"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by TheWindsWraith on 2007-05-27
Can someone help me out with this no screens found error in xorg?  I used Wubi to install Ubuntu Studio, and I can't seem to start Xorg... I'm stuck in the terminal... What do I do?

---

### Post by taurus on 2007-05-27
Reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by TheWindsWraith on 2007-05-27
I've tried to reconfigure using:

sudo dpkg-reconfigure xserver-xorg

I don't see the driver that I need in there... Should I use i810?

---

### Post by taurus on 2007-05-27
Yes.  Use i810 (or even vesa) until you get X up and running again.

---

### Post by TheWindsWraith on 2007-05-27
I get a different error now... I used vesa...

"XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining."

---

### Post by TheWindsWraith on 2007-05-27
I tried 810 and it worked! thanks, now how do I get the resolution right? and where do I get the 945gm drivers?

Thanks for all of your help by the way...

---

### Post by wrongo on 2007-06-08
i810 isn't working for me

and i'm getting

"[ 1073.456000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

followed automatically by

[ 1092.700000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

what do i do?

---

