---
title: "qmake?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by thrakirr on 2006-02-28
I'm trying to build MythTV 0.19 from source, and ./configure results in
```
./configure: line 2958: qmake: command not found
```
I looked around and qmake is supposed to be built in when Qt is built.. how come the command doesn't work? 
Is there a work-around for this, or a package?
Any help would be appreciated.

And yes, I know mythtv-0.18 is installable through Adept. Already have that working, just want to upgrade.

---

### Post by Pragmatist on 2006-02-28
run synaptic and install: qt3-dev-tools   if it isn't already installed.  That should give you qmake anyway.  The way I found it is by running synaptic, doing a search using the keyword qmake

---

### Post by thrakirr on 2006-02-28
Awesome, solved. Thanks!

---

