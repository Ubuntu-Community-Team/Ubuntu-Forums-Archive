---
title: "Synaptic won't open"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by thomasboleyn on 2008-04-18
Hi there, I tried to run synaptic package manager a minute ago, but received this error instead:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the program.
E:_cache->open()failed, please report.

I ran the first part in apostrophe's in the terminal and it offered me loads of options that I didn't really understand. 

Any help would be greatly appreciated, thanks!

---

### Post by Michael.Godawski on 2008-04-18
Run this in terminal

```
sudo dpkg --configure -a
```

---

### Post by Danikar on 2008-04-18
This looks similar to the problem you are having.

[http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/](http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/)

---

### Post by forrestcupp on 2008-04-18
> **Michael.Godawski said:**
> Run this in terminal

```
sudo dpkg --configure -a
```

Right.  The error output doesn't tell you to use **sudo** which is needed.  Try it again like Michael posted.

---

