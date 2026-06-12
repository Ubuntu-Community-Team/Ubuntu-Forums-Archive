---
title: "problem with &quot;bars&quot; when initiated"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by DrummerHead on 2007-07-07
Ok, sometimes when ubuntu starts, the... "bars" aren't there, they are just... gone. It must be because of beryl. I'm wandering if it is there a terminal command to make them show, initiate or whatever.

[[IMG]http://img234.imageshack.us/img234/751/screenshot2lc9.th.png[/IMG]](http://img234.imageshack.us/my.php?image=screenshot2lc9.png)

Also, when Ubuntu starts it asks me for a password. That's fine, but it does so in a 1600x1200 resolution, and then it finally goes to 1280x900 (because that is the resolution I actually use). Is there a way to change that initial resolution to 1280x900?

---

### Post by annda on 2007-07-07
as to bars/panels: you can start them with gnome-panel. press ALT+F2 to get a window where you can enter the command.

as to resolution: edit your xorg.conf and remove 1600x1200.

```
gksudo gedit /etc/X11/xorg.conf
```

---

