---
title: "how to create custom theme for login window"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-11
I am new to Ubuntu but am getting very frustrated with creating my own login window. I know that in order to change your login window you have to go to system/administration/login window.


I have a picture file which is a jpg and I want to be able to make it my login picture. I would greatly appreciate if you could tell me the steps in detail about how to actually make a custom login window and make it work for png or jpg. Thank you.

P.S. I already know about [http://www.gnome-look.org/](http://www.gnome-look.org/) but it hasn't really helped.


:popcorn:

---

### Post by aysiu on 2007-02-11
I would download a GDM theme from Gnome-Look.org, untar it (double-click and extract), and then replace whatever parts you see (images, etc.) with your own images. Then re-tar it and install it.

Or use Alt-F2 ```
gksudo nautilus
``` and go to /usr/share/gdm/themes and modify the themes directly.

---

### Post by ardchoille42 on 2007-02-11
Yeah, most people just take a gdm login theme apart and learn from the various components. I have made a lot of gdm themes and that's how I started. If you learn a bit about the different components, you'll end up teaching yourself how to make you own.

I wrote a short tutorial a while back which gives some good info. It's not complete, but it will explain some things.

[http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome212.GdmThemes](http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome212.GdmThemes)

---

### Post by lanchongzi on 2007-02-21
stupid question  :(

i have a .jpg file, but here they use .png files.
is it ok to use my .jpg, or do i have to change it to .png
...and how do i do that ( just searched the Synaptic Package Manager without results :()

thank in advance

---

