---
title: "sudo make install"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-28
Whenever i run that command this is what it always says for EVERYTHING that requires me to use that command. This is what it says:

make: *** No rule to make target `install'.  Stop.

What do you think the problem is? And how can the problem be resolved? Can it be resolved  if instead of using "sudo make install" I use "sudo checkinstall"?

Thanks in advance!

---

### Post by Steveway on 2007-10-28
Did ./configure and make run without any errors?

---

### Post by limac on 2007-10-28
a similar thing happens with make.

It says:

make: *** No targets specified and no makefile found.  Stop.

For ./configure i think it's ok.

---

### Post by eapache on 2007-10-28
Do you have the package build-essential installed? It is required for make and make install to function properly.

---

