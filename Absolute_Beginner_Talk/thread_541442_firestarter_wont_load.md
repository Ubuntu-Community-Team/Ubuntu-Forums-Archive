---
title: "firestarter wont load"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-09-02
System->Administration->Firestarter
Just hangs and never loads. It does show the app in the task bar for a few seconds.
> antsvr@antubuntu:~$ firestarter
antsvr@antubuntu:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:9710): Gtk-WARNING **: cannot open display:

---

### Post by Dr Small on 2007-09-02
Try:
```
gksudo firestarter
```

---

### Post by ant2ne on 2007-09-02
> **Dr Small said:**
> Try:
```
gksudo firestarter
```Well with that command I don't get an error message, but the &%(@ thing still refuses to load

---

### Post by Seisen on 2007-09-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/30291](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/30291) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Could be related to this.

---

