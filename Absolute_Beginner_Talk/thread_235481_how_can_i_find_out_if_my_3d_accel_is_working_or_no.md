---
title: "how can i find out if my 3d accel is working or not?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by SkippyJames on 2006-08-13
hi all,

i downloaded the latest nvidia-glx driver package and i want to check if the 3d acceleration is working or not.. is there a command to check that from the commandline or anywhere else?

thanks for your help

---

### Post by infoseeker on 2006-08-13
Try this ----->
> glxgears -printfps

This will indicate whether nvidia-glx has been setup correctly or not :)

---

### Post by Jeroen Vernooij on 2006-08-13
Also, if you enter ```
glxinfo
``` **direct rendering** is set to: Yes

---

### Post by Iesos on 2006-10-25
or... you can run an coded movie with say mplayer, and move the mouse pointer over the running movie. If the shadow of the ponter turns blue, you got your accelleration going.

---

### Post by jd65pl on 2006-10-25
This will give you just the information you require
```
glxinfo |grep render
```

---

