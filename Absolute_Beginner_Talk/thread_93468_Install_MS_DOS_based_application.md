---
title: "Install MS DOS based application???"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Robroy11976 on 2005-11-22
Hi, need help ... how could i install my old dos programs???  It's actually an accounting program for my my store which i was using for a long time already, but i would like to install it on ubuntu coz it's much more stable and of course, less virus which means less troubles ...

---

### Post by Pablo_Escobar on 2005-11-22
> sudo apt-get install dosbox

dosbox is a nice program whih allows You to run Dos based programs.

Usage :
f.e. dosbox /home/pablo/games/betrayal  -   launches dosbox and mounts the selected dir as drive C:

---

### Post by Robroy11976 on 2005-11-22
Thanks ... would you happen to know where i could find guides for dosbox??? I mean how to use it more???

---

### Post by Brunellus on 2005-11-22
Google is your friend.

[http://dosbox.sourceforge.net/wiki/index.php](http://dosbox.sourceforge.net/wiki/index.php)

Also, once you install the dosbox package, executing 

```
$ man dosbox
``` 

from a console will give you the dosbox manual page.  It's pretty good, as I remember.


In general:
you can copy the installation files for your application to a new directory on your ubuntu system.  Then, run dosbox, telling it to use the directory where the install files are located as "C:\" for the virtual DOS system.

---

