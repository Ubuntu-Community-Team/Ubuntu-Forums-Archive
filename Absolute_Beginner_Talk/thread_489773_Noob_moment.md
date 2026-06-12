---
title: "Noob moment"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Morhas on 2007-07-01
Ok whenever I try to install sometihng, I get this error 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I have a feeling this is a quick fix, but I can't seem to figure it out. Any help would be greatly appreciated. Thanks.

---

### Post by AndyCooll on 2007-07-01
Have you tried doing what it says? Running from a terminal the following:
```
sudo dpkg --configure -a
```

:cool:

---

### Post by Morhas on 2007-07-01
Forgot the sudo lol. Thanks man.

---

### Post by vexorian on 2007-07-01
I got that problem when trying to install a virtualbox .deb I killed the deb installer it broke everything.

If you remember the last .deb you installed (or tried to install) before this started happening then you have to use dpkg to force remove that package.

---

