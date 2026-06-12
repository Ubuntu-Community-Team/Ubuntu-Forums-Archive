---
title: "Anybody know how long it takes a new Nvidia driver to get to the Repositories"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by C.S.Cameron on 2007-09-21
Anybody know how long it takes a new Nvidia driver to get to the Repositories?
I see there is a new driver our for the 8 series cards, (100.14.19), wondering how long before I can trust Envy to install them. 
Hope they are as much fun as the last ones, kept me entertained for weeks.

---

### Post by Pumalite on 2007-09-21
Why don't you install from here: [http://www.nvidia.com/object/unix.html?](http://www.nvidia.com/object/unix.html?)
Just follow the instructions.

---

### Post by C.S.Cameron on 2007-09-21
Have you tried it? did it work?
I tried that last time, Could not get anything to work till envy.
Will give a shot at the new drivers tomorrow, after I recall where I backed up my latest xorg.conf.
I am trying to get up the courage to try the new down load page on auto. [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

---

### Post by Pumalite on 2007-09-21
Ctrl+Alt+F1
login with your username
your password
sudo /etc/init.d/gdm stop
sudo sh /path/to/the/driver/NVIDIA-Linux-x86 blah, blah, blah
sudo /etc/init.d/gdm start
If need be: startx

---

### Post by C.S.Cameron on 2007-09-22
Thanks Pumalite.
I tried Envy first, but it still tries to install the old drivers.
Then I tried your method.
Dang, it worked the first time, sort of takes all the fun out of Linux.
Cork

---

