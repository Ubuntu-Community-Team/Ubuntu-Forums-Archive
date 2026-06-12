---
title: "blank screen when resuming from sleep"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-26
Running dual-boot vista/7.10 on a Lenovo T61 laptop C2D 2.0GHz - when i resume from sleep, the screen is simply blank. I can tell the screen is actually on, but it is blank. I have no choice but to restart. What gives? Resuming form sleep in windows is fine. I am pretty sure that the appropriate drivers are installed for the video.

---

### Post by spiderbatdad on 2007-12-26
i have noticed under the power management settings, one option put the display to sleep, another put the computer to sleep. On my thinkpad, I have set put computer to sleep "never" put display to sleep "30 minutes." I think resuming from the former may require Fn-F4...or something like that. Whereas resuming from display sleep only requires hitting a key or moving the mouse.

---

### Post by spiderbatdad on 2007-12-26
Update...just tried it. Fn-F4 toggles putting computer to sleep and resuming from computer sleep.

---

### Post by TheNorthWaves on 2007-12-26
i've been using fn-F4 - no such luck

---

### Post by nick_h on 2007-12-26
> I can tell the screen is actually on, but it is blank.
Is the screen being blank the only problem? Does the computer appear to be working otherwise?

Start by reading the [HowTo: Fix suspend and hibernate on laptops](http://ubuntuforums.org/showthread.php?t=471855) thread.

---

### Post by TheNorthWaves on 2007-12-26
Is there a way that the problem can be addressed without suspending the sleep mode? Sleep mode is a pretty crucial part of my laptop's daily grind. Oddly I recall sleep mode working correctly when I used the Ubuntu live CD (before I installed it)

---

### Post by nick_h on 2007-12-26
If it is just the screen not waking up correctly then s2ram can be a useful tool to debug the problem.  When you work out what options are required you could try changing some of the settings in /etc/default/acpi-support.

---

