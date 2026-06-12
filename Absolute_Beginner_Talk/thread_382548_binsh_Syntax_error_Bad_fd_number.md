---
title: "/bin/sh: Syntax error: Bad fd number"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-12
I posted this in [This thread]("http://www.ubuntuforums.org/showthread.php?p=2283928#post2283928"), but that was 11 hours ago and no response :(

When trying to do a "make" for cdemu I get this error.

```
glasgowm@glasgowm-desktop:~/cdemu-0.8$ make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_core.o
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_mod.o
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_proc.o
  LD [M]  /home/glasgowm/cdemu-0.8/cdemu.o
  Building modules, stage 2.
  MODPOST
  CC      /home/glasgowm/cdemu-0.8/cdemu.mod.o
  LD [M]  /home/glasgowm/cdemu-0.8/cdemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic
```

---

### Post by Bachstelze on 2007-03-12
Try this :

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```

---

### Post by auraithx on 2007-03-12
Thanks that worked, 

I followed this tutorial
[http://www.ubuntuforums.org/showthread.php?t=276743](http://www.ubuntuforums.org/showthread.php?t=276743)

and created a script to mount. When I right click --> mount image I get a error stating

"You cannot mount any more images" 

:confused: :confused:

---

