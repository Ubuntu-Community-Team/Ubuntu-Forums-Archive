---
title: "[SOLVED] CPU temp readout in tray"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by BigJules on 2006-12-04
Anyone heard of a motherboard/CPU temperature readout pgm suitable for a Gnome tray? About the only thing I miss from those Windoze days...

---

### Post by aum11 on 2006-12-04
I use Gkrellm for temperature info.  It also has many other services.

It is not in the tray, but maybe it will be of good service.

---

### Post by yabbadabbadont on 2006-12-04
Sensors-applet is a gnome-panel applet that will display various temp/fan stats.  It is in the universe repository.  The one in the repos for dapper is broken for some people though.  (including me) The same version built from source worked though.  It had something to do with libsensors3.  Give it a try.  If it works for you, good, if not, uninstall it.  Currently, I use gkrellm for all my sensors display.

---

### Post by BigJules on 2007-09-12
SOLVED - lm-sensors did it for me!

---

