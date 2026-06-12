---
title: "need to know what graphics driver i have"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-02-03
well i installed edgy and now im trying to install beryl but i want to know what graphics driver i have.  im sure its the aiglx but i want to make sure.  im also using a mobility radeon m6 ly video card.  not sure if its 3d compatible or not, i havent seen it on any lists for beryl compatible or non compatible stuff.  any help is appreciated.  thanks

---

### Post by shareMenaPeace on 2007-02-03
To check for XGL 

```
glxinfo | grep direct
```

AIGLX
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

XGL
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

---

### Post by dragnazz5.0 on 2007-02-03
when i put in that command i get this.  what does that mean?

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

ive currently got a dual boot with edgy installed on both partitions.  im using one as a guinea pig right now...and the x window system is crashed.  i followed the instructions on the aiglx page you linked and it crashed the x window system.

---

### Post by shareMenaPeace on 2007-02-03
What error did you get during crash? Can you run "beryl-manager" from terminal?

---

### Post by dragnazz5.0 on 2007-02-04
when i run it from terminal it opens but i cant switch to beryl.  it says "fatal error no screens found"

---

