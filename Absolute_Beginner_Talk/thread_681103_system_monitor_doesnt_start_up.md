---
title: "system monitor doesnt start up"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by DamagePlan on 2008-01-28
Doesn't start up.

Whats the problem?

thanks
DP

---

### Post by Ub1476 on 2008-01-28
Try to run it in the terminal:

```
gnome-system-monitor
```

---

### Post by DamagePlan on 2008-01-28
Nope

/home/richard/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:63: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/richard/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:64: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/richard/.themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:65: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

** (gnome-system-monitor:6655): WARNING **: SELinux was found but is not enabled.

Floating point exception (core dumped)

---

### Post by Ub1476 on 2008-01-28
Might have something to do with your theme configuration. This has been posted at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087"). Look at the latest post.

---

