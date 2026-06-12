---
title: "power management"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-05-28
hi all...

how to enable power management on ubuntu...

i have powernowd installed but i dont know to setup it....my cpu is celeron m..is it supported?how to lower the cpu freq when using battery?and how to lower the monitor brightness automatically?

pls help:) :) :)

---

### Post by joshrobinson on 2006-05-28
[QUOTE=TheTux]hi all...

how to enable power management on ubuntu...

i have powernowd installed but i dont know to setup it....my cpu is celeron m..is it supported?how to lower the cpu freq when using battery?and how to lower the monitor brightness automatically?

pls help:) :) :)[/QUOTE]

mine automatically dims the brightness when i unplug the power cord, have you tried that on yours?

---

### Post by Sutekh on 2006-05-28
For GNOME:

First open a Terminal (Applications -> Accessories menu), and use this command, allows you to set frequency
```

sudo chmod +s /usr/bin/cpufreq-selector
``` Then right-click a panel and choose Add to Panel, and add a CPU frequency scaling applet.

You can use this to change CPU frequency behaviour (governor) or change frequency directly.

---

### Post by TheTux on 2006-05-28
i did that and a msg box popup :

CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine......

why? is it because of my cpu - celeron m..does anybody with this cpu having the same problem?

---

### Post by Sutekh on 2006-05-28
You can check if your CPU allows frequency selection.

What is the output from
```
cat /proc/cpuinfo
``` The key option is the **stepping **option.

---

### Post by TheTux on 2006-05-28
stepping is 8....freq scaling works on windows. so it is the cpu problem or powernowd doesnot support celeron?

---

