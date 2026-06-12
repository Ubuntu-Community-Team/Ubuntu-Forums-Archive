---
title: "2 beginner's questions"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Poogy on 2007-04-13
Hi Everyone,

I have two small beginner's questions:
1. Installation of new programs:
I've notcied that if I install new programs via the add/remove program GUI, everything works fine, and the new programs are installed correctly - meaning, they are now added to the ubuntu menues and if required to run at startup they do so.
however, if I install software using command line, for example:
```
sudo apt-get install firestarter
```
The applicaions are indeed installed, but I don't see them on the menu, and I think they also don't run on startup.
Am I doing something wrong or is this a normal behaviour?

2. Adding startup programs that require root permissions:
I've tried to add a new program (the no-ip client) to the list of startup programs (via the Sessions menu in the Ubuntu Preferences menu. This program requires to be run as root, so I've added the command ```
sudo noip2
``` to the startup list.
However, I think the program is not starting during startup and I'm guessing that it's since the sudo command requires me to add the root password each time I run it manually. 
So how is it possible to add such programs to the startup programs list?

Many thanks in advance!

---

### Post by Seisen on 2007-04-13
Firestarter can be found in System>Adminstration>Firestarter.

---

### Post by sonny on 2007-04-13
For the second question, I used to have a no-ip account and I added the service just as a normal start-up (without the sudo) and it worked ok.

As for the first question, firestarter should be in System>Admin>Firestarter menu, so looking for it in the apps menu won't work. As for other programs I haven't experienced the things you say, they all install fine, perhaps you should try using synaptics package manager instead of the command line.

---

### Post by lamalex on 2007-04-13
firestarter may appear to not start at boot, but firestarter isn't actually a firewall, the firewall is built into the Linux kernel, firestarter is just a GUI for controlling it, although it can be done more effectively through CLI and the "firewall" shorewall.

---

### Post by Seisen on 2007-04-13
Shorewall isn't exactly the best things for a newb to using because its so complicated to use. Firestarter is the easiest one to use, the setup is self explanatory.

---

### Post by lamalex on 2007-04-13
shorewall taught me how to really use linux to the fullest ;)

---

