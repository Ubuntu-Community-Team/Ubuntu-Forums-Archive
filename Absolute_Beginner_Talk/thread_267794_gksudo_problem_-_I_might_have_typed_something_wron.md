---
title: "gksudo problem - I might have typed something wrong"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-29
Hi I typed the following in my root shell

```
export DISPLAY=:0.0
```

so when I typed "gksudo gedit /etc/exports" it gave the following error:

```
Xlib: connection to ":0.0" refused by server Xlib: No protocol specified (gksudo:11251): Gtk-WARNING **: cannot open display:

```
How do I solve this problem????

---

### Post by henriquemaia on 2006-09-29
If you run things as root from a standard terminal under X, they will open nicely without having to export DISPLAY.

Unless you want to run things from the tty.

---

