---
title: "xgl almost bricked my computer!"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-08-23
I was trying to install xgl and now x and xgl doesn't work! I'm stuck in the commnad line with no GUI! Normally this would be fine, but almost all of the programs I use have a GUI. EX: amarok, banshee, gimp, and lots more. Help would be greatly appreciated.

---

### Post by bulldog on 2006-08-23
I hope you where clever enough to make a copy of your xorg.conf before you altered it?

If you did replace xorg.conf with that copy.:) 

If you did not make a copy try:

sudo dpkg-reconfigure -phigh xserver-xorg

from the command line and reboot.

If this won't work you must undo the changes you made to your xorg.conf manually.
Try sudo nano /etc/X11/xorg.conf and undo the changes you made and terminate with CTRL-x and see yes to save the fyle as your xorg.conf.

Hope this work's for you.

---

### Post by Tomosaur on 2006-08-23
Your computer is far from bricked if you can use the command line. In fact, it's a lot more powerful :P. 

Anyway, are you sure it wasn't the recent, bugged X update which did it? If so, there is a new update available which should fix the problem. You can download it from aptitude, or use wget, or whichever tool suits your fancy :)

---

