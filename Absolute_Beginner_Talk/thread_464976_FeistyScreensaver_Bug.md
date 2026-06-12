---
title: "Feisty/Screensaver Bug?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-06-05
Okay, here's the situation, and it's been repeatable and consistent. If I'm running anything for internet radio (Rythmbox or Streamtuner/XMMS), and the screensaver kicks in, the system freezes. The song on the radio warbles back and forth just like a scratched CD does, the monitor goes blank, and the system no longer responds to the keyboard or mouse. I cannot return to the normal screen from the screensaver, and I cannot kill either the screensaver or the music program. I can only force a reboot via the power switch, and when the system is done rebooting after this experience, I have no sound at all. If I reboot a second time using the icon, everything returns to normal. For the moment, I've turned off the screensaver (sniff! Great graphics!); but how do I go about reporting a bug?

Thanks!

---

### Post by SomethingCronic on 2007-06-05
I have this problem as well, only since upgrading to Feisty, and only on 'some' screensavers. For now I've just had to turn off 'random' and select screensavers I already know don't freeze my system.

---

### Post by silkstone on 2007-06-05
I'm not sure but it could be a processor issue. If you add the System Monitor to one of your panels, you can see the processor usage. Then System>Preferences>Screensaver and click on them while watching what the processor is doing. Some of the screensavers run the CPU at almost 100%! If you choose one that has low usage, that may be OK.

---

### Post by wmichaelb on 2007-06-06
Hmm...if SomethingCronic above is having a similar problem with a 2.2 GHz dual core processor with 1.5 GB of RAM and a separate video card, it seems unlikely that it's a performance issue. But thanks to both of you, and I'll file a bug report.

---

### Post by Cerealbh on 2007-06-06
i have feisty and Braid screen saver locks my entier computer, just going to the screen savers app and if ic hoose braid it will lock up my computer, ill be fileing a bug report as well, this is the only that i have problems with but its very anoying when i come back and all i see is 1/2 a design and can't get out of it

---

### Post by yusufk on 2007-06-11
Hi,

I have a somewhat different problem, I cannot recover from the screensaver, I just get a black screen with the mouse pointer. I've had to go to a terminal (ctrl-alt-f1) and do a ps -e|grep screensa
I usually see two gnome-screensav apps running and have to kill both.

What can the problem be?

---

### Post by bigken on 2007-10-29
> **Cerealbh said:**
> i have feisty and Braid screen saver locks my entier computer, just going to the screen savers app and if ic hoose braid it will lock up my computer, ill be fileing a bug report as well, this is the only that i have problems with but its very anoying when i come back and all i see is 1/2 a design and can't get out of it

yep braid also lock my desktop :confused:

---

