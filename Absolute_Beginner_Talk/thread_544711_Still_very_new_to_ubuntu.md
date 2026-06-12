---
title: "Still very new to ubuntu"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by vanishedchic86 on 2007-09-06
I tried installing sunjava and it seemed to install fine, when I went to install frostwire it wouldn't allow me to do it saying some other update manager was running still. I tried going into Synaptic and I got the error message

[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/B]

When I run 'dpkg --configure -a'  in the terminal it tells me **dpkg: requested operation requires superuser privilege**

any help would be appreciated

---

### Post by mikewhatever on 2007-09-06
Just run 'sudo dpkg --configure -a'.

---

### Post by Gremlinzzz on 2007-09-06
put sudo  in front of command

---

### Post by jnorthr on 2007-09-06
sudo dpkg --configure -a
may do it though you will be asked for your superuser password.

---

### Post by nonewmsgs on 2007-09-06
if you have add/remove, synaptic, or automatix running, it will give you an error.  if you arent' and it does, i would log out and come back and it ought to be fixed.

to run as a superuser type sudo before the commands. like i have below.  


sudo dpkg --configure -a

---

### Post by WebSiteGuru on 2007-09-06
> **vanishedchic86 said:**
> I tried installing sunjava and it seemed to install fine, when I went to install frostwire it wouldn't allow me to do it saying some other update manager was running still. I tried going into Synaptic and I got the error message

[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/B]


Di you closed sunjava installation? It still think you had that open.

> **vanishedchic86 said:**
> When I run 'dpkg --configure -a'  in the terminal it tells me **dpkg: requested operation requires superuser privilege**

any help would be appreciated

try this:

```
sudo dpkg --configure -a
```

---

### Post by vanishedchic86 on 2007-09-06
that worked and fixed the problem but now it won't let me open frostwire, even though it was installed

---

### Post by rsambuca on 2007-09-06
Try to open frostwire from a terminal.  Just type 

frostwire

If it doesn't open, the terminal should tell you what is happening.

---

