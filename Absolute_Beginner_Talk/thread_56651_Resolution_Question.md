---
title: "Resolution Question"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-13
How can I change the screen resolution of the Login Screen and the Splash one?

---

### Post by Muhammad on 2005-08-13
Don't tell me it's impossible... :mad:

---

### Post by aysiu on 2005-08-13
[QUOTE=Muhammad]Don't tell me it's impossible... :mad:[/QUOTE] It probably isn't impossible, but it also probably can't be done easily. Is the screen resolution so big you can't even read the log-in info?

---

### Post by GreyFox503 on 2005-08-14
I had a similar problem with my login screen being at the wrong refresh rate than my desktop.  The solution involved adding custom lines to my xorg.conf file, at /etc/X11/xorg.conf

There are several threads on this forum on how to do that.  You might be able to fix it the easier way by running this:

```
sudo dpkg-reconfigure xserver-xorg
```

this is a way to configure your xserver by choosing options about your graphics card and monitor.

When it gets to the part about choosing resolution, there will be three choices, something like:

Easy
Medium
Advanced

I don't remember the exact wording.  If you choose medium, then you can specify your monitor's resolution and refresh rate.

---

### Post by Muhammad on 2005-08-15
Problem Solved, Thanks. :)

---

