---
title: "Backlit Keyboard Issues MBP"
date: 2007-09-22
forum: Apple Intel Users
---

### Post by Arkillion on 2007-09-22
After looking through a lot of threads it seems many people can't get their keyboard to light up. Mine is always lighting up even when I don't want it to. Anytime I start a new session, unplug, or plug in the power cord, the backlight in the keyboard turns itself back on to the highest setting regardless of the lighting conditions of where the laptop is. I can use the F8 F9 and F10 keys to control it but I hate having to constantly turn it off.

Is there anyway to make it work more OSX like? Where it only turns itself on when its dark and doesn't reset itself whenever there is a change in the power cord or session?

Thanks.

---

### Post by cyberdork33 on 2007-09-22
> **Arkillion said:**
> After looking through a lot of threads it seems many people can't get their keyboard to light up. Mine is always lighting up even when I don't want it to. Anytime I start a new session, unplug, or plug in the power cord, the backlight in the keyboard turns itself back on to the highest setting regardless of the lighting conditions of where the laptop is. I can use the F8 F9 and F10 keys to control it but I hate having to constantly turn it off.

Is there anyway to make it work more OSX like? Where it only turns itself on when its dark and doesn't reset itself whenever there is a change in the power cord or session?

Thanks.
The mactel patches should be trying to implement this correctly. What kernel / Ubuntu version are you using?

---

### Post by Arkillion on 2007-09-22
Thanks for the reply.

I'm using Ubuntu 7.04 and my kernel is 2.6.20-16-generic

---

### Post by cyberdork33 on 2007-09-22
> **Arkillion said:**
> Thanks for the reply.

I'm using Ubuntu 7.04 and my kernel is 2.6.20-16-generic
There was a good revision to the mactel patches regarding the applesmc package since then. It improves power usage and some of the sensors like the light sensor and accelerometer. Gutsy will be full release in a month, I would check out the newer kernels in there before sending much time on what you have now.

---

### Post by xIke on 2007-10-16
Hopefully someone's still watching this thread.

I'm running gutsy, and my keyboard is full brightness every time I restart.  Any way to make it just remember where it was previously?

---

### Post by ronocdh on 2007-10-17
> **xIke said:**
> Hopefully someone's still watching this thread.

I'm running gutsy, and my keyboard is full brightness every time I restart.  Any way to make it just remember where it was previously?
I have the same experience, had it since Feisty. IIRC, the backlit didn't reliably work in Edgy, but maybe I'm wrong.

I'm with Cyberdork: wait for Gutsy final and try it out, they're implementing a lot of Mactel changes, which both surprises and delights me.

---

### Post by xIke on 2007-10-19
Does anybody know a shell command to set the brightness of the backlighting?  If there is one, then I could at least run that at login to turn the backlighting off (99% of the time I don't need it.)

---

