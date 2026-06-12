---
title: "ctrl-alt-canc to lanuch system monitor with gnome/compiz"
date: 2007-03-01
forum: Art &amp; Design
---

### Post by romaluca on 2007-03-01
I have ubuntu with compiz 0.3.6
The combo ctrl-alt-canc for launch system monitor not works with compiz.

in a post I have read that from terminal i must type:

gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command1 "<Ctrl><Alt><Delete>"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command1 "gnome-system-monitor"

but this not works.
How i can do?
Thanks

---

