---
title: "How do I export environment variables to the Alt+F2 launcher?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-25
I have a certain GUI based program that I use that will only run correctly if a certain environment variable is set and exported before I call the program.  I have a line in my .bashrc that exports this variable, and when I call the program from a terminal window, everything works fine.  But if I call it from the Alt+F2 program launcher, it messes up.  How can I get the environment variable to set/export itself on login in such a way that the Alt+F2 program launcher is also aware of it?

---

### Post by Sparkster185 on 2007-05-25
Would it work if you exported the variable and executed the command at the same time?  Separate the two commands with a semi-colon.

export MY_VAR=my_value; command

?

---

### Post by lazyart on 2007-05-25
A bash script that exports it and run it on startup (session)?

Or a bash script that exports the variable, then calls the gui program?

---

