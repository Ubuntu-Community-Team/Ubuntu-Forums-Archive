---
title: "Resricted Driver"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-31
intel wireless driver is restricted?

also I dont think the graphics driver is working correctly
I cant enable effect
New gateway m6824 with a 128mb ati graphics card?

---

### Post by Ub1476 on 2007-12-31
My Intel network card is restricted, so it might be your is as well (if that was your question?).

Before messing with the driver for your grphic card/controller post the output of:

```
lspci | grep VGA
compiz
```

---

### Post by frenchsquared on 2007-12-31
found driver here
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

gordon@Gateway:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c8
gordon@Gateway:~$ compiz

---

### Post by frenchsquared on 2007-12-31
also no sound?

---

### Post by Ub1476 on 2007-12-31
Take a look [here]("http://ubuntuforums.org/archive/index.php/t-608547.html") for your graphic card. It's a bit messy, but it looks like it worked for some.

Make sure nothing is muted (right click on the volume control) and also look in System>Preferences>Sound. If you have an Intel card this might help too: [/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by frenchsquared on 2007-12-31
here link didnt work

sound button says no audio divises installed

I downloaded the ati installer but I have no idea what to do with it

---

