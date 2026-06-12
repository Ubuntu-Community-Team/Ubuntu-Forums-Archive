---
title: "need help identifying graphics card"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by bionnaki on 2006-03-23
I have installed ubuntu with xfce on a friends computer. he has an nvidia graphic card installed but is unsure of what exact model he has. how I can pull up the specs in xfce?

the computer is still a bit slow (why I'm using xfce over gnome) and I suspect it is because the driver is not installed among other reasons (little ram - he's at 128mb).

thanks!

---

### Post by bluevoodoo1 on 2006-03-23
From a terminal, see if... 

```
sudo lshw
```

or

```
lspci
```


can help.

---

### Post by bionnaki on 2006-03-24
oh wow. sudo lshw is quite helpful. thanks!

---

