---
title: "firestarter not starting"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-08-29
I have firestarter installed, and want to run it, but the GUI doesn't pop up, either through the shortcut or the terminal. I need to allow port 465 (for email), but this is at the moment impossible for me. Here is the terminal output:

```

scott@scott-laptop:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:19253): Gtk-WARNING **: cannot open display:  
```

I am running an up to date Feisty. Any help is appreciated.

---

### Post by deadgobby on 2007-08-29
Do not use sudo to run firestarter. Just type in 

firestarter

Gobby

---

### Post by kellemes on 2007-08-29
[http://www.howtoadvice.com/AutoFirestarter/]("http://www.howtoadvice.com/AutoFirestarter/")

---

### Post by rouge568 on 2007-08-29
Problem solved. I followed the link, and changed the buggy line. I also removed the "NOPASS" line, because I think it may have been part of my problem. Thank you.

---

