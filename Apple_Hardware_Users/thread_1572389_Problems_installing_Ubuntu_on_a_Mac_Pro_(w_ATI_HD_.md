---
title: "Problems installing Ubuntu on a Mac Pro (w/ ATI HD 4870 gpu)"
date: 2010-09-11
forum: Apple Hardware Users
---

### Post by tdes on 2010-09-11
So I've been trying to set up triple boot onto a last generation Mac Pro with an ATI HD 4870 GPU, so I can do cross platform compilation for a project I'm working on (MilkyWay@Home if any of you are also interested in volunteer computing).

I've already set up all my partitions, so in that regard I'm good to go, however none of the installation CDs seem to work.

If I use the regular one, it shows me the splash screen with the keyboard and little dude on the bottom, and then a cursor then the monitor goes black (as in off).

If I use the alternate installation CD, I can get to the main menu, but when I select install then the screen goes black (again as in off).

I've tried adding 'vga=771' to the end of the boot command, to force it into VGA mode, but the same problem happens. I've also tried using 'xforcevesa' with the same result. Removing 'quiet' and/or 'splash', as well as trying 'nosplash' also give me the same problems, although certain variations give me a couple seconds of text flying by on the screen before the screen goes off.

I've also tried installing WUBI from the windows partition -- and again with the same error.

The only other thing I can think of is that maybe it doesn't like using the mini display port in the ATI GPU. I could try and find another monitor and use the DVI output, but if there's something else I should be trying (I'm pretty much a n00b when it comes to linux), I'd really love any kind of input. I've been banging my head against the machine all day.

I'm also open to trying other flavors of linux, if another one might work better.

---

### Post by Optimus Prime on 2010-09-11
Sounds like the radeonhd driver isn't initializing your card correctly.

Try disabling it by setting a bogus parameter like 'radeonhd.tdes=true'.

If that works, you can install ATI's fglrx driver once the system is installed.

---

### Post by tdes on 2010-09-11
> **Optimus Prime said:**
> Sounds like the radeonhd driver isn't initializing your card correctly.

Try disabling it by setting a bogus parameter like 'radeonhd.tdes=true'.

If that works, you can install ATI's fglrx driver once the system is installed.

No luck.  So the boot line was something like:


"... quiet splash -- radeonhd.tdes=true"  (just to double check i did that right)

And I got a second of a blinking cursor than the screen shut off again.  Do I need to do something like not have a space between the -- and radeonhd.tdes=true ?

---

