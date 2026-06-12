---
title: "Updating a change"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-09
how does one update a change made to ```
/etc/modprobe.d
```
so that each time i don't have to save and reboot

---

### Post by ggaaron on 2007-06-09
Modprobe this modules manually?

---

### Post by pardesi on 2007-06-09
> **ggaaron said:**
> Modprobe this modules manually?

sorry i couldn't get what you said .is there any alternative

---

### Post by ggaaron on 2007-06-09
modprobe.d is the file with modules that get autoloaded on boot, am I right?

So if you add anything to this file run:
modprobe ModuleToBeAdded
and if you delete:
modprobe -r ModuleToBeDeleted

---

### Post by ggaaron on 2007-06-09
Sorry, wrong file=P

modprobe -r module && modprobe module

this deletes and loads the module again.
There may be problems with modules that are used... Ubuntu's kernel doesn't have force module unload, so when changing such modules I think that you have to restart.

---

### Post by pardesi on 2007-06-09
can't this be automated

---

### Post by ggaaron on 2007-06-09
From what I know in this directory you can change what actually happens when you load a module - options and so on. I only hope, that it really does that=P

But probably the modules are already loaded, so for the changes to take place you have to reload them. Auto module reload after changing a file wouldn't be the best option...

Please correct me if I'm wrong.

---

