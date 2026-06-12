---
title: "icewm default start button [Resolved]"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2006-12-09
every time i start icewm i get the default icewm start button. how can i use the start buttons that other themes use?

---

### Post by aysiu on 2006-12-09
> **cosmoshell said:**
> every time i start icewm i get the default icewm start button. how can i use the start buttons that other themes use?
The IceWM start button is defined by the theme you're using.

If you go to the actual theme folder, you can see it:
/usr/share/icewm/themes/*themename*/taskbar/icewm.xpm

I believe if the theme does not define the image, IceWM will default to this one:
/usr/share/icewm/taskbar/icewm.xpm

---

### Post by cosmoshell on 2006-12-09
the theme im useing has its own start button. the only one i see is the one that says debian and its the same for all my themes.

---

### Post by aysiu on 2006-12-09
The Debian one is probably /usr/share/icewm/taskbar/icewm.xpm

But if your theme has its own start button, it should be in /usr/share/icewm/themes*themename*/taskbar/icewm.xpm

---

### Post by cosmoshell on 2006-12-10
thanks i got it working by changeing its linux.xpm to icewm.xpm naby im useing a newer version of icewm or something.

---

