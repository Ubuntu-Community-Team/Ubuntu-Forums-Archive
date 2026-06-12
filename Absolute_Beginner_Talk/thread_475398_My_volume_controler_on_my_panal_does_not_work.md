---
title: "My volume controler on my panal does not work"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-16
Even when I mute it. I still hear everything.   I guess it's better than windows when I would have it up all the it wouldn't make any sound. Is there anyone out there that can help me please?

---

### Post by Lapino on 2007-06-16
Have you checked that you are controlling the master volume of the right audio device using the volume control in the taskbar.
Try this:
1. Right-click on the volume icon and select "preferences"
2. Select the device that corresponds to your primary audio device
3. Choose "Master" in the list below it.

I don't know if this will help, but it's the first thing that popped into my mind when reading your problem.

---

### Post by tgalati4 on 2007-06-16
It would help to give us some more information:

What version of Ubuntu?
What is your hardware?

In a terminal, post the output of:

aplay -l

and

lspci -vv

---

