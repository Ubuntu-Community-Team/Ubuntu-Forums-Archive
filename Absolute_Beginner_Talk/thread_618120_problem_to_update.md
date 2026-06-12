---
title: "problem to update"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by hilfer on 2007-11-20
hi all:

Next to a freeze during an update, when I try to update again i get the following error message:

E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache ->open () failed, please report.

what to do now ???

hilfer.

---

### Post by AlexenderReez on 2007-11-20
run 


> sudo dpkg --configure -a

---

### Post by hilfer on 2007-11-20
> **AlexenderReez said:**
> run

Done.

So if I understood right, everytime I have to run a command I have to enter first : sudo ??

---

### Post by Anicka on 2007-11-20
You have to use sudo if the command you run installs or configures any program or setting in you system. For running normal programs like text-editors you don't need it. If you're not sure whether to use sudo or not, try first without, if you get an error message saying something like "Are you root?" you need to run the command with sudo.

---

