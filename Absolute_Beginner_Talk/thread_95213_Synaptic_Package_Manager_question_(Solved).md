---
title: "Synaptic Package Manager question (Solved)"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Sonic5688 on 2005-11-26
Hello yet again :D . I was just wondering where the executable files go once theyre installed by the SPM? I installed some programs using it and can't find them :rolleyes:

---

### Post by Xian on 2005-11-26
Most but by no means all of them go in /usr/bin.

---

### Post by aysiu on 2005-11-26
You don't need to know where the application lives in order to run it (this is true in Windows as well). If you open up a Run dialogue and type in *firefox*, Firefox will run. If you type in *gnome-terminal*, the Gnome terminal will run.

---

### Post by Sonic5688 on 2005-11-26
Is there a way to find out where a specific file was installed? I'm sorry for asking such simple questions.


Okay, forget this question. Thanks for the help!

---

### Post by Xian on 2005-11-26
[QUOTE=Sonic5688]Is there a way to find out where a specific file was installed? [/QUOTE]
For example:

```
$ whereis realplay
realplay: /usr/bin/realplay /usr/lib/realplay 
```

---

### Post by joselin on 2005-11-26
With which command too.

```

$ which totem
/usr/bin/totem

```

---

### Post by Sonic5688 on 2005-11-26
This forum has solved yet another one of my problems. Thanks much! :razz:

---

