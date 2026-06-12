---
title: "Quick need Help with Adept Manager"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by mr.waldo on 2007-10-10
OK so when I open Adept Manager everything works fine but when I Click manage repositories it crashes and all it says is We're sorry; software-properties crashed.

Does anyone know what could be wrong.

 I also put in a screen shot hope it helps
[IMG][[IMG]http://img394.imageshack.us/img394/6216/snapshot1in9.th.png[/IMG]](http://img394.imageshack.us/my.php?image=snapshot1in9.png)[/IMG]

---

### Post by mr.waldo on 2007-10-10
has know one ever had ever this problem.

---

### Post by swisscow on 2007-10-10
Don't know why this happens but you can manage the repositories through the command line:

```
kdesu kate /etc/apt/sources.list
```

Putting #'s in front of a line comments it out - i.e. it is ignored.

IMO Synaptic is much easier to use - it's always the first thing I install when setting up Kubuntu - use Adept to install it :)

---

### Post by mr.waldo on 2007-10-10
thamks i need to manage the repositories so i can update to the beta 7.10. If I update do you think it will fix itself

---

### Post by swisscow on 2007-10-10
Well I've just done a clean install of gutsy and checked for your problem and everything works as it should. Can't speak whether an update would make it go away though.

---

### Post by mr.waldo on 2007-10-10
do you know how to update through Synaptic with Kubuntu

---

### Post by swisscow on 2007-10-10
Updates are still handled by Adept - you get the update icon appearing, click, type in your password, download list of updates and install - easy as pie!

---

