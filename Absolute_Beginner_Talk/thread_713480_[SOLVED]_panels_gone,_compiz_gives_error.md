---
title: "[SOLVED] panels gone, compiz gives error"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-03-02
Compiz won't start anymore, and the panels are gone.

One of my screenlets is stuck on my destkop (instead of on the widget layer).

I've been installing new themes for a while and this happened after setting a new skydome.

I've rebooted, didn't do anything.

If I do compiz --replace in a terminal this is the error:

$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
libpng error: Read Error

[[IMG]http://img99.imageshack.us/img99/6425/screensz9.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screensz9.png)

Any help is appreciated.

---

### Post by billgoldberg on 2008-03-02
I got compiz working again by going to ccsm using alt+f2 and removing the skydome, but my panels are still gone.

I don't have a clue how to add i've there isn't already one on the desktop.

[[IMG]http://img340.imageshack.us/img340/2282/screen2lg3.th.png[/IMG]](http://img340.imageshack.us/my.php?image=screen2lg3.png)

---

### Post by billgoldberg on 2008-03-02
And it seems all the screenlets on the wigdet layer are gone expect one.

What happened?

---

### Post by billgoldberg on 2008-03-02
Problem solved.

I reinstalled the the panels in synaptic and after logging back in everything was ok.

For future readers:

open up a terminal and reinstall "gnome-panel"

[[IMG]http://img126.imageshack.us/img126/4152/screen3oh6.th.png[/IMG]](http://img126.imageshack.us/my.php?image=screen3oh6.png)

---

