---
title: "Change XFCE Desktop Icon Spacing"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-15
Is it possible?
How do I do it?

---

### Post by fred.warren on 2008-03-23
Icon spacing is controlled by xfwm4. Although there is a configuration dialog for xfwm4 you will have to specify these settings in the file .config/xfce4/xfwm4/xfwm4rc as noted in [http://www.xfce.org/documentation/4.2/manuals/xfwm4#hidden_options](http://www.xfce.org/documentation/4.2/manuals/xfwm4#hidden_options)

[http://www.math.unizh.ch/sepp/xfce-3.5.2-ds/](http://www.math.unizh.ch/sepp/xfce-3.5.2-ds/) shows there are 2 commands

IconGrid
IconSpacing

So in .config/xfce4/xfwm4/xfwm4rc you would put something like
IconGrid=8
IconSpacing=8

Or you could run the command

xfwm4 IconSpacing=8

---

