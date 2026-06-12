---
title: "C compiler?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by benner on 2006-08-04
i tried to install the following 3 programs:
jazz++ (midi sequencer)
kmobiletools
openvpn

the install instructions were pretty straightforward

	./configure
	make
	make install

but after configure, i got

no acceptable C compiler found in $PATH

i downloaded/installed a c compiler using adept (i can't remember the name of it) and i saw another one on add/remove programs that seems to come installed with kubuntu, but i guess they don't work or i need to do something different.  is there one specific one i should get?  different command in kubuntu?

---

### Post by Sutekh on 2006-08-04
Easiest way is to install the build-essential meta-package, that includes the GNU C Compiler (gcc) and other tools like make.
```
sudo apt-get install build-essential
``` Will do it all for you.

---

### Post by benner on 2006-08-04
thanks

---

