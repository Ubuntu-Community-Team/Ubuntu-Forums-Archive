---
title: "won't let me edit /etc/usplash.conf"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Thumper! on 2007-12-18
hi there....

i'm trying to change my usplash.conf settings from 

xres=1280
yres=1024

to

xres=1024
yres=768 

So i change it but it won't let me save, say i don't have permission....yes i am the admit and it's my laptop so how can i change my account settings so that i can edit anything!

Thanks, Tom
:guitar:

---

### Post by lamalex on 2007-12-18
```
gksudo gedit /etc/usplash.conf
```
in terminal

---

### Post by erfahren on 2007-12-18
```

gksudo gedit /etc/usplash.conf

```
we use "gksudo" since gedit is a GUI application (sudo *will* work for that but using gksudo for GUI apps is a good habit to get into)

otherwise:
```

sudo nano /etc/usplash.conf

```
"nano" is a command line text editor. check it out sometime  -you may need to use it someday in a pinch :D

---

### Post by Thumper! on 2007-12-18
cool thanks guys....worked ;)

---

