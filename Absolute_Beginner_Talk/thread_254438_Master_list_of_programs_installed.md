---
title: "Master list of programs installed?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-09-10
So, when I install programs from the synaptic package manager, most of the time I can go to either applications, system/preferences or system/administration (graphically) and i will see the program that I just installed.  A few of them however, do not show up.  I am guessing they are accessable throught the command line, but I don't have the faintest idea how to start them up that way.

I have dug around quite a bit, but this question seems to be too simple to warrant much explaination, so I post here.

Any ideas on how to get a master list of the programs on my dapper system,graphically or command line wise?  I am guessing there is a menu command, and from there I could track down these wayward applications I have installed, but have not seen hide nor hair of.

Thank you, community!

---

### Post by orb9220 on 2006-09-10
go to synaptic and bottom left you will see filters which one is installed apps

---

### Post by seelk on 2006-09-10
> **orb9220 said:**
> go to synaptic and bottom left you will see filters which one is installed apps

Is there a way to get a printout of that list?  Maybe an output to a text file?

---

### Post by jordanmthomas on 2006-09-10
```

dpkg --list >> installed_packages

```
will print out all installed packages to a file named installed_packages

**edit**
Notice, though, that this is not a list of all the programs you can run.
This would be
```
ls -a /usr/bin >> all_programs
```
That would get the bulk of the programs you can run.

---

