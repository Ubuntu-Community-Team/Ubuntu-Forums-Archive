---
title: "How do I prevent tomboy from displaying notes on startup? (2)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-18
I posted this topic before and thought I found a solution for it, but those solutions appear to have been flukes and do not work consistently at all.  So I'm reopening this question:

Right now, I have Tomboy notes set to start up at login, but everytime I log in, tomboy pops up with the window containing all my notes. I'd rather only have the panel applet start on login and only have that window show when I call it myself. Knotes displays the same sort of behavior--when I have it set to start on login, it automatically generates a new note on login. How can I change it so that the note applications only start themselves in the panel without popping up new notes or windows that I didn't ask for?

---

### Post by bloodniece on 2007-05-18
You may be able to change it either by writing a plugin or changing some app parameters in gconf-editor.

Type ALT+F2 then type ```
gconf-editor
```Go to --> Apps --> Tomboy
and 
Schemas --> Apps --> Tomboy

There seems to be some stuff there to play with. Good luck.

---

### Post by laptoplinux on 2007-05-20
Ok, fixed the problem.

[http://ubuntuforums.org/showthread.php?p=2691900#post2691900]("http://ubuntuforums.org/showthread.php?p=2691900#post2691900")

(RESOLVED)

---

