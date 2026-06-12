---
title: "Screens blank before startup"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-10-22
When I log on there is a slight break when I first log on and my desktop appears. The screen is just blank for awhile until my desktop appears. It isnt a hardware issue, like a lack of memory or like its lagging out, but like it is some setting...anyone know anything about this? BTW, I can see my cursor, its just the rest of the screen is black.

---

### Post by Jorn.jambers on 2007-10-23
I think its just your desktop initialising so dont see the problem.

Kind regards

---

### Post by NilsE on 2007-10-23
If your concerned that you don't get the progress splash screen between login and desktop  check out this thread

[http://ubuntuforums.org/showthread.php?t=588114](http://ubuntuforums.org/showthread.php?t=588114)

---

### Post by stuh84 on 2007-10-23
Other option is

Go into a terminal and type in

> sudo gedit /etc/usplash.conf

And in there you should see "xres" and "yres". Change them to the same values as your screen resolution. Then in a terminal type

> sudo dpkg-reconfigure usplash

When you restart, everything should be there and working

---

### Post by toasty_ghosty on 2007-10-23
Thanks. They were too small and it was causing issues. Thanks for the help everyone.

---

