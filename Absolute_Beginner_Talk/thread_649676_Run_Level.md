---
title: "Run Level"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stunningman on 2007-12-25
DOES anybvody know how to change run level?
i want the run level to change to init3.

---

### Post by taurus on 2007-12-25
Do you want to kill X server because you need to install a driver for your graphic card?

Press <Ctrl><Alt>F2 and log in with your name and password.  Then, run

```
sudo /etc/init.d/gdm stop
```
That would stop the GUI login screen.

---

### Post by The Cog on 2007-12-25
You can change the runlevel to 3 with this command:
**sudo init 3**

But you will notice that is doesn't do anything. In Ubuntu (and debian I think), all the runlevels are the same (2 is the default). Why are you trying to change runlevel? What is it that you actually want to do?

---

