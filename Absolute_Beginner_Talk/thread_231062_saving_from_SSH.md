---
title: "saving from SSH"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-08-06
So I'm trying to save a php file from a school server onto my computer, lets call it 'test.php'. i'm accessing the server through SSH. I know this should be easy but looking through a bunch of command stuff online for a couple of hours hasn't helped. I could just copy and paste from terminal but there must be a better way. 

I tried the 'cp' thing but since, in the terminal, i am on the server, it doesn't recognize the path to my comp:
 cp <path>/test.php /home/me/desktop/test.php

i'm sure this can't be hard...i'm just blonde. Any help is much appreciated.

Thanks,

Maria

---

### Post by simonn on 2006-08-06
scp

---

### Post by Maria_Firewire on 2006-08-07
hey thanks! :)

---

### Post by davebgimp on 2006-08-07
Some handy links for you:

[http://en.jakilinux.org/apps/ssh-tricks/](http://en.jakilinux.org/apps/ssh-tricks/)

[http://www-it.desy.de/support/help/uco_documentation/sshhowto.html](http://www-it.desy.de/support/help/uco_documentation/sshhowto.html)

---

