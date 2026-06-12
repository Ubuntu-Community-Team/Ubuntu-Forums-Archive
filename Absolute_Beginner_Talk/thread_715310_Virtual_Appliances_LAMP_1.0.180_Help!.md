---
title: "Virtual Appliances LAMP 1.0.180 Help!"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by jezter on 2008-03-04
I installed a VMWare virtual machine to use as a local test platform for my website. Everything appeared to install fine, I was able to log-in to to the apche server and the configuration screen and all is good.
It uses Ubunto 6.04 and everything I read on the documentation indicates that once installed I should find myself in a Gnome GUI but I'm not. How do I find out how to start Gnome or if it is even installed. The documentation of the virtual machine claims its a standard Ubuntu install so I would assume Gnome is installed somewhere.

---

### Post by freelinuxhelp on 2008-03-08
I assume that you log in on a terminal. If so, try this command: startx

Lots of people don't install xwindows on servers, so it may not be included on your virtual machine.

---

