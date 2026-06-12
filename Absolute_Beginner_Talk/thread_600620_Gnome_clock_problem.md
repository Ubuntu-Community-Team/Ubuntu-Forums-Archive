---
title: "Gnome clock problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-11-02
I've switched from fluxbox to gnome recently, but I hate the look of gnome clock=/ I'd like it to be:
"year.month.day hours:minutes"
but it is something like:
"Fri Now 2, 17:36"
Can this applet be customized? I can't find any options=/

Thanks in advance
Aaron

---

### Post by lpb331 on 2007-11-03
If you open the configuration editor and go apps - panel - applets - clock_screen0 - prefs, two of the keys are format and custom_format. If you set format to custom, you can then edit custom_format to %Y %B %d  %I:%M to give you year month day  hours:minutes (12 hour clock). If you want to change the way it looks, just search strftime; the first result gave me a nice table of variables to use.

---

### Post by ggaaron on 2007-11-03
Thanks! =)

---

### Post by lpb331 on 2007-11-03
No problem!

---

