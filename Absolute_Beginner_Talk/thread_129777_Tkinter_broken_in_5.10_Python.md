---
title: "Tkinter broken in 5.10 Python?"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Horza on 2006-02-14
I've had problems with using Tix in a Python-Tkinter app, in that python claims to be unable to find the Tk library upon executing a statement such as

 root = Tix.Tk()

The app works fine with the Active State version of Python (2.4.2), which makes me suspect that there might just be something wrong with the Ubuntu setup.

---

### Post by cwaldbieser on 2006-02-14
[QUOTE=Horza]I've had problems with using Tix in a Python-Tkinter app, in that python claims to be unable to find the Tk library upon executing a statement such as

 root = Tix.Tk()

The app works fine with the Active State version of Python (2.4.2), which makes me suspect that there might just be something wrong with the Ubuntu setup.[/QUOTE]
I am not familiar with Tix, but I can write/run simple Tkinter programs without a problem.  Maybe the Tix package isn't importing Tkinter symbols into its namespace?

---

### Post by Horza on 2006-02-15
I don't know what's wrong yet (I don't really know either Tix or Tkinter very well).  If nobody who really does know shows up, I'll take it to some of the more advance forums, w/b good to have it fixed for Dapper.

---

