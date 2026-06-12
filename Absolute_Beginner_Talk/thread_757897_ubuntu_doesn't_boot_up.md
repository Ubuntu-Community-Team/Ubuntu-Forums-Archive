---
title: "ubuntu doesn't boot up"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by hiro nakamatty on 2008-04-17
right, im new to Ubuntu, but this is what i have done, i have a Nvidia graphics card, and i changed the resolution of the screen by using; system, administration, screen and graphics, 
i apologize for any mistakes but i am currently having to run on windows:(
i turn on my computer, the dual boot grub comes on, i go onto Ubuntu, it like, does the Ubuntu starting thing with the Ubuntu logo, and the loading bar.
the screen then goes black, and i get a message.
the last line of the message says that is is running something but nothing happens from then onwards.
im really stuck! please help!:confused::confused::confused:

---

### Post by TeoBigusGeekus on 2008-04-17
Boot into recovery mode from the grub menu and type
```
sudo dpkg-reconfigure xserver-xorg
```
to readjust your settings.

---

### Post by dstew on 2008-04-17
At the black screen, press ctrl-alt-F1. That should get you a command line. On the command line enter```
sudo dpkg-reconfigure xserver-xorg
```This gets you a text-based program to reconfigure your desktop. Answer the questions the best you can. Usually the default answers are correct. When you get to the part about the display, see if you can change back to your original resolution. If that doesn't work, do the reconfiguration again, but choose the vesa driver, and a lowish resolution, say 1024 x 786. That should at least get you a desktop. Then you can try to get the nvidia driver working again.
EDIT: If you reconfigure from recovery mode, as recommended above, start the desktop with```
startx
```If you do it from the first terminal (ctrl-alt-F1) restart the desktop with ctrl-alt-backspace.

---

### Post by hiro nakamatty on 2008-04-17
thanks everyone!!! the code worked perfectly! im am now back on ubuntu!!!!
thanks thanks thanks
:guitar::guitar::guitar::lolflag::lolflag::guitar::guitar::guitar:

---

