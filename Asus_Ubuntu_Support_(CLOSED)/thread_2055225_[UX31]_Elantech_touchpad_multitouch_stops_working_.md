---
title: "[UX31] Elantech touchpad multitouch stops working for no reason"
date: 2012-09-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Nosferax on 2012-09-08
Hey,

I'm using the UX31 with the latest Ubuntu (12.10) and my elantech touchpad's multitouch supports seems to break after some unidentified event. I'm not going to sleep, just using the laptop and then, bam scrolling with two fingers no longer works, also mid/right click by finger tapping also.

I don't know what is causing this, it was happening in 12.04 as well, just less often. Now it's very frequent (and very annoying).

What can cause this? Where can I report it? 

Anyone else experience this?

Thanks.

EDIT: I just found out that one finger taps are not recognized either, making the matter not only about multitouch. It's not about finger detection because the clickpad is able to detect 1-2-3 fingers just fine when I click.

---

### Post by edjski on 2012-09-10
> **Nosferax said:**
> Hey,

I'm using the UX31 with the latest Ubuntu (12.10) and my elantech touchpad's multitouch supports seems to break after some unidentified event. I'm not going to sleep, just using the laptop and then, bam scrolling with two fingers no longer works, also mid/right click by finger tapping also.

I don't know what is causing this, it was happening in 12.04 as well, just less often. Now it's very frequent (and very annoying).

What can cause this? Where can I report it? 

Anyone else experience this?

Thanks.

EDIT: I just found out that one finger taps are not recognized either, making the matter not only about multitouch. It's not about finger detection because the clickpad is able to detect 1-2-3 fingers just fine when I click.

I'm not sure if this will help but give it a try.
The problem I experience is an occasional lock-up of my cursor -it stops responding. When that happens, I hit "ctrl-alt-T" to bring up a terminal and then type "synclient TouchPadOff=0".
This causes my cursor to respond to input from the touchpad.
Typing "synclient" in the terminal brings up all the variables and current values. Synclient has many many variables to play with but information is available via Google search.

FWIW, I use "synaptiks" as the gui to adjust my touchpad settings and at the moment, I have to run it everytime I boot and de-select "automatically switch touchpad off on keyboard activity", hit "apply" then re-select the same setting and hot "apply" again. -I'm not sure why the settings are not persistent.

Hope this helps, good luck!
-Ed

---

### Post by emgiezet on 2012-11-27
Have same issue on mine Vostro 3560. Touchpad  is also elantech.  Glitches, jumps, says clicked and finally not working at all.

---

