---
title: "How change Wi-Fi icon?"
date: 2008-01-05
forum: Art &amp; Design
---

### Post by ggod on 2008-01-05
I want change Wi-Fi icon on toolbar, but i can`t find where it`s on HDD.

Can you show where i can find it, to exchange?

I mean this:


[[IMG]http://img223.imageshack.us/img223/2791/screenshotdp9.th.png[/img]](http://img223.imageshack.us/my.php?image=screenshotdp9.png)

---

### Post by ggod on 2008-01-05
help!!:guitar:

---

### Post by NilsE on 2008-01-05
The name of the icon is nm-signal-xx.png where xx =00, 25, 50, 75,and 100.  They are located in a sub folder called /status/ in the icons folder

/usr/share/icons/THEMENAME/  #THEMENAME is the name of the theme you have active.

They could be in any one of the sub folders like scalable, 22x22, etc. but more than likely in the status sub folder of one of theme.

easy way to find them is go to the icons folder in Nautilus and search for nm-signal

---

### Post by phenest on 2008-01-05
I found them in /usr/share/icons/hicolor/22x22/apps

---

### Post by NilsE on 2008-01-05
> **phenest said:**
> I found them in /usr/share/icons/hicolor/22x22/apps
Unless you add an icon theme they are the only ones there by default so you can replace them with whatever you like.

---

### Post by ggod on 2008-01-05
O! thank you very mach!:KS

---

