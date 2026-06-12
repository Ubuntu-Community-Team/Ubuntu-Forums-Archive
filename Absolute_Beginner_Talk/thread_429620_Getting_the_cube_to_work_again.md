---
title: "Getting the cube to work again"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-05-01
I have been using Ubuntu 7.04 now for one day and I took my laptop to college today, one of my mates went to change the desktop wallpaper but selected the desktop effects option instead and disabled the cube. I then enabled the cube again but it will not show, can anyone assist me. Is there maybe a way of starting it in Terminal because it aint enabled when i say for it to be. Cheers!

---

### Post by etank on 2007-05-01
Try this. Open a terminal and type```
gconf-editor
```That should open a window. Expand apps->compiz->general->screen0->options. In there you should see something called hsize. change from a 1 to a 4. Close the window and try the cube. hsize is what controls the number of sides on the "cube". If you used 3 you would get a triangle for example.

I hope that makes sense and works for you.

---

### Post by Ozeuss on 2007-05-01
You might want to try gnome-compiz-manager. I like that alot better than the 'desktop effects" window, and is more configurable

---

### Post by webjames on 2007-05-01
if that fails try this:
```
sudo apt-get install beryl beryl-manager
beryl-manager
```

that should start beryl, and you should have a diamond in your tray where you can look at the settings. if you right click that icon then you can select a window manager, metacity is the default gnome manager, but beryl is the 'cube' select beryl if it is not already selected.

you might also check that you have the restricted driver installed, goto settings restricted driver management and make sure your grfx driver is enabled.

hope this helps, any problems post back

---

### Post by thecomputingexpert on 2007-05-01
cheers that works brilliantly, how do you get it to start at startup though?

---

### Post by Grungydan on 2007-05-01
Go here:  [https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29#head-19456dc30b20dd54ec0af8428cd2d1ad0a5ad1a0](https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29#head-19456dc30b20dd54ec0af8428cd2d1ad0a5ad1a0)

---

### Post by thecomputingexpert on 2007-05-01
cheers!

---

