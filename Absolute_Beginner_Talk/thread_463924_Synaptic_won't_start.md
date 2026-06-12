---
title: "Synaptic won't start"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jpennin5 on 2007-06-04
Everytime I try to start synaptic it looks like it is going to run for a few seconds, but then it just stops and doesn't open anything.  When I run 'sudo synaptic' in the terminal it says a previous version is running and it is trying to bring it the foreground.  It says this even if i restart my computer and it is the first thing I do.  It will still let me download updates from the terminal.  I have already tried removing and re-installing synaptic, but it didn't fix anything.  Also, I haven't been able to add/remove applications, or change my supported languages.  Any help would be appreciated

---

### Post by bapoumba on 2007-06-04
hello,
What does **ps aux | grep synaptic** return ?
If you have synaptic processes running other than the grep processus itself, you can **sudo killall synaptic** or **sudo kill <pid_of_process>** to kill them individually.

---

### Post by jpennin5 on 2007-06-04
i've been trying to run those commands, but now synaptic just keeps freezing on me...even in the terminal  :(

---

### Post by bapoumba on 2007-06-05
Please paste in here the complete output to:
```
gksudo synaptic
```

---

