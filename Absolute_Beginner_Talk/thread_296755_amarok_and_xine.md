---
title: "amarok and xine"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-10
Help me, I have tried to follow the advice in this forum of setting up amarok, because one day it randmly started saying unable to initialize xine audio, so I tried this:

mv ~/.kde/share/config/amarokrc ~/.Trash

and now it doesnt work at all, when I try to run it it says initialising database in a little window and then nothing...!

I love this program and have to have it back, anyone know how?

---

### Post by ciscosurfer on 2006-11-10
Have you tried reinstalling?

---

### Post by tommy1987 on 2006-11-10
no how do I do this?

Also, it works fine if i run it as root, but obviously this is no long term fix.

---

### Post by ciscosurfer on 2006-11-10
Reinstall```
sudo aptitude reinstall amarok
```

---

### Post by tommy1987 on 2006-11-10
reinstall does nothing for me, the only change I have made has been the console line above.

---

### Post by ciscosurfer on 2006-11-10
Reinstall amarok-xine```
sudo aptitude reinstall amarok-xine
```or if you don't have this package, substitute 'reinstall' with 'install'.

---

