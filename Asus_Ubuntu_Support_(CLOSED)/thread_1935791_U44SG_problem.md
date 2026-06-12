---
title: "U44SG problem"
date: 2012-03-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by sanz on 2012-03-05
I just bought an Asus U44SG, with i5-2450 and nVidia610M. Surprisingly, it came with only a free dos. But it's better for me, if it did cut down the price. I erased the full dsk and installed Ubuntu 11.10. I used many distros of Ubuntu before and 10.04 for almost 2 years with satisfactory on my previous Dell D620.

I think this model is very similar to U36SD. So I dug into the looong post of U36SD and followed almost every tweaks. But now I'm still have these problems.

1. suspend does not work. it freezes after the lid is closed. I have to reboot with power button. (fixed already. shamefully i forget to chmod the script file. but the "magic time" issue seems remains)
2. after modifying the "915 grub" thing, power consumption was lower from 22xxxmw to 19xxxmw. But after installing BumbleBee 3.0, I found the power consumption rise from 19xxxmw to 34xxxmw. The bbswitch shows "OFF" status.
3. when typing here or in terminal, sometimes the cursor moves forward with my stoke but with blank, just like I typed a "space". But if I make a scroll, those missing characters are shown, or if I just enter in termial, the command is okay. So it's definitely a display problem. This is very annoying and I do not know when it will occur. 

Other minor issues does not upset me much. Help with these 3 main issues will be appreciated.

---

### Post by sanz on 2012-03-05
Another problem is the auto-dim of dispaly. with auto-dim on battery, the display kept changing from 100% to 70% or so, and then back to 100%. Even when I am moving the cusor, it changes to 100% after I change it manually to 50%. I had to disable auto-dim function.

---

