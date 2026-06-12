---
title: "how to correct gdm configuration"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by banga on 2007-12-24
hi friends

i am new in ubuntu7.10

when i start my pc

when only command prompt is open
gdm is not open and an error is display on screen
which is

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>.>>>>>

server authorized directory (dacmon/serrauthdir) as set to /var/lib/gdm but does not exit.
please correct gdm configuration and rrestart gdm

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

plz help me
thanks in advance

---

### Post by dward526 on 2007-12-24
attempt the following from the command line

```
 sudo aptitude reinstall gdm 
```

This will reinstall gdm and we will see if this works.

---

### Post by banga on 2007-12-24
it is not working
bcz i have no internet connection
i have live cd(ubuntu7.10)

---

### Post by dward526 on 2007-12-24
Just to clarify,

You have no internet connection while using the live cd?

---

