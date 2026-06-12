---
title: "beryl error"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by kaboom on 2006-10-31
Hey all

I followed this how-to for installing beryl on edgy:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

i got all the way through and then at the final step; 'beryl -manager' 

this was my error message:
kaboom@kaboom-laptop:~$ beryl -manager

XGL Absent, checking for NVIDIA

Nvidia Absent, assuming AIGLX

libGL warning: 3D driver claims to not support visual 0x5b

beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

beryl: Couldn't load plugin '-manager'


after that i could type in messenger boxes, but couldn't move windows around and once something got covered up by another window i couldn't get back to it.  once i rebooted it was back to normal, and happens each time i try 'beryl -manager'

i'm using an hp pavillion dv4000   with an intel i810  graphics card

any idea what i am doing wrong?
thanks in advance for your help
'boom

---

### Post by po0f on 2006-10-31
kaboom,

beryl-manager, one word.
```
$ beryl-manager
```

---

### Post by kaboom on 2006-10-31
that did the trick thanks a bunch

---

