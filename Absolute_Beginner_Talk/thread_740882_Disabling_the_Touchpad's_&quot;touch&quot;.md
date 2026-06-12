---
title: "Disabling the Touchpad's &quot;touch&quot;"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-03-31
I just wanted to know where can I disable the "touch" of the touchpad??? I once had it in the Mouse option but now it isnt there...Dont know why...Any help???

---

### Post by abhiroopb on 2008-03-31
[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/)

maybe that will help

---

### Post by Toddy on 2008-03-31
Install Gsynaptics.  Then edit xorg.conf:

sudo gedit /etc/X11/xorg.conf

add
Option 'SHMConfig' 'true'
inside the section synaptics. 

Then you will be able to disable the Touchpad via a GUI

---

### Post by Michl on 2008-03-31
Just a footnote that this is not surefire recipe.  It works
on some laptops and not others.  So if this does not
work for you, that doesn;t mean you're doing something
wrong.

---

