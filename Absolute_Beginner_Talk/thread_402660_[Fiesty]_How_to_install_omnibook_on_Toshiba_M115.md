---
title: "[Fiesty] How to install omnibook on Toshiba M115"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Vega on 2007-04-06
how do I install this application to get my fn keys for brightness and others working?

thanks

---

### Post by Vega on 2007-04-09
anyone?

---

### Post by sebos69 on 2007-04-10
well it's kind of easy : 

-get the last tarball from omnibook.sf.net
-extract it

in a console, get into the extracted directory and type:
make
sudo make install

sudo modprobe omnibook

if it works, you can append "omnibook" to the list of modules to load at startyp in : /etc/modules

---

### Post by Vega on 2007-04-13
> **sebos69 said:**
> well it's kind of easy : 

-get the last tarball from omnibook.sf.net
-extract it

in a console, get into the extracted directory and type:
make
sudo make install

sudo modprobe omnibook

if it works, you can append "omnibook" to the list of modules to load at startyp in : /etc/modules

I was successful in "sudo make install" but when I typed in "sudo modprobe omnibook" I get this message in terminal "FATAL: Module omnibook not found."

keep up the good work!

---

### Post by sebos69 on 2007-04-13
maybe try "sudo depmod -a" before.

---

### Post by Vega on 2007-04-13
> **sebos69 said:**
> maybe try "sudo depmod -a" before.

alright, I typed in my pass and allot of hdd activity was going on, what do I do now?

---

### Post by sebos69 on 2007-04-13
read this : 
[http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibook](http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibook)

and this:

[http://omnibook.sourceforge.net/doku.php?id=readme#how_to](http://omnibook.sourceforge.net/doku.php?id=readme#how_to)

---

