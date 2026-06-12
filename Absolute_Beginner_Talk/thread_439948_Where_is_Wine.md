---
title: "Where is Wine?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-05-11
I have downloaded Wine. I know because *Synaptic* tells me so.
Now, how do I launch it? Then how do I add it to the applications menu or put a launcher on the desktop?

---

### Post by Happy_Man on 2007-05-11
you don't "launch wine' on its own; you use it in conjunction with a windows app.
But if you have just installed wine, you'll need to configure it. Run the following command in a terminal (Applications --> Accessories --> Terminal):
```
winecfg
```

That'll get you started.

---

### Post by Najand on 2007-05-11
You can just type:
```
wine ~~~~~~.exe
```
to execute ~~~~~~~.exe

---

### Post by Jonne on 2007-05-11
Or doubleclick it, as you would on Windows.

---

### Post by Neil Purling on 2007-05-11
What did I do wrong?

neil@neil-desktop:~$ wine ~~~~~~.exe
wine: could not load L"c:\\windows\\system32\\~~~~~~.exe": Module not found
neil@neil-desktop:~$

---

### Post by Najand on 2007-05-11
You should change ~~~~~~.exe with your exe file.

---

