---
title: "Gnome panels"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by waqas_butt0071 on 2007-02-27
if i delete the two default panels on desktop, how can i get them back ?

---

### Post by Sentinel83 on 2007-02-27
waqas,

can you hit Alt+F2 to get a terminal, then type - 

killall -gnomepanels 

hit enter, and see if it restarts the gnomepanels module

I think that is the correct syntax, someone correct me if I'm wrong, thanks.

---

### Post by kinematic on 2007-02-27
assuming you still have a terminal on your desktop
> gnome-panel
that should work.

---

### Post by waqas_butt0071 on 2007-02-27
i tried the 

alt+f2 

and wrote

xterm

and then

killall gnome-panel

but it refresh only if there is any panel on the desktop

---

### Post by kinematic on 2007-02-27
what about alt>f2 gnome-panel ?

---

### Post by bapoumba on 2007-02-27
> **waqas_butt0071 said:**
> if i delete the two default panels on desktop, how can i get them back ?
Right click on top of your screen > new panel.
If they have been deleted, you will have to add back all the applets and menus (Right click again > Add to panel).

---

### Post by waqas_butt0071 on 2007-03-08
well i have the panels now but i have a problem :

whatever windows i minimize it disappears.

what is happening????

---

### Post by Perfect Storm on 2007-03-08
You have to add **window list** to the panel.

---

