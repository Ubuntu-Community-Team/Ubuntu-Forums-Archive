---
title: "/etc/Xll/xorg.conf empty?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by vendetta23 on 2007-09-03
im follinw this: [http://ubuntuforums.org/archive/index.php/t-207794.html](http://ubuntuforums.org/archive/index.php/t-207794.html)

to install a video card driver

however, when i type in gksudo gedit /etc/Xll/xorg.conf, it is empty....

whats wrong with this?!

---

### Post by st33med on 2007-09-03
I think it isn't supposed to be two 'l' it is supposed to be two '1'.

ex. /etc/X11/xorg.conf

---

### Post by Bachstelze on 2007-09-03
Try with /etc/X11/xorg.conf instead ;)

EDIT : pwn3d :(

---

### Post by isaacj87 on 2007-09-03
I think you put *I* instead one *1*

try this:

```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by vendetta23 on 2007-09-03
ohhhh

so theyre one's not el's...

:D

---

### Post by st33med on 2007-09-03
:cool: Can't touch this! :cool:

---

### Post by nowshining on 2007-09-03
ur typing it in wrong most likely :) i have no xorg.conf I deleted mine in an attempt to recreate it but it didn't re-create, however everything is working fine for me for NOW i gotta wait to see with my newer card..

open up a terminal
type gksudo nautilus
don't worry if it gives an authentication error that's normal at time and it's a knwon bug
as soon as nautilus comes up
lef side click file system
scroll down click the X11 folder (it's two one's an x and two one's by the way)
find xorg.conf and double click it - click display if it asks u what to do...

---

### Post by nowshining on 2007-09-03
wow you guys beat me to it..lolz :) i gotta do some typing exercises..

---

### Post by por100pre1 on 2007-09-03
[SIZE="2"]STOP! Don't forget to backup the xorg.conf file before editing it.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Everybody, do it even if you're not going to edit it! You could need this backup someday. Better safe than sorry. :cool:[/SIZE]

---

### Post by Paul133 on 2007-09-03
And while you're at it, remove the useless file you created. 
```
sudo rm /etc/Xll/xorg.conf
``` (those are l's not 1's.)

---

