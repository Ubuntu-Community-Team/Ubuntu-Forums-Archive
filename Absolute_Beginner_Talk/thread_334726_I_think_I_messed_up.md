---
title: "I think I messed up"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-01-09
I think I  may have screwed up my system.

I was working on installing the Nvidia drivers to enable Twinview.

I installed the legacy drivers for my geforce2 (I am pretty sure its legacy,  but I am not sure).  I editing the settings in xorg from 'nv' to 'nvidia,' after backing it up, and I restarted the system.  

I now get a blue screen saying X has failed to start do you want to see the server output.  After this I get what looks like a terminal screen with only a blinking cursor.  Thats all, no option to login and no commands are recognized.

Did I screw myself and do a clean install or is there a built in safety I can use to try and fix it?

---

### Post by riven0 on 2007-01-09
When you get to the terminal screen, just log in and do **sudo dpkg-reconfigure xserver-xorg** and it should fix it for you.

EDIT: Oh, yeah. To get to the terminal screen try hitting CTRL + ALT + F1

---

