---
title: "Need list of installed apps and CLI command to launch them."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Chilli Bob on 2007-11-29
Is there an easy way to get a list of installed apps and in particular, the command line instruction to launch them,  E.G. Typing "firefox" at the command line launches firefox, but what do I type to launch OO.o calc etc???

The reason I need this is to set up my menu in IceWM,

---

### Post by rax_m on 2007-11-29
You can see which apps are installed in the Add/Remove programs .. and selecting "installed applications" from the dropdown menu. 

The executable names are usually stored in /use/bin 

But you'll have to link the executable to the program manually, unless someone has a better way.

---

### Post by UnixAnt on 2007-11-29
As previously mentioned, the actual binaries are stored in /usr/bin

If you change to this directory and execute the following:

ls -l >/home/YOURUSERNAME/binlist (or whatever you wish to name it)

Then you can use a text editor (gedit, vi, etc) to view the particulars of the installed executables by opening the newly created text file: /home/YOURUSERNAME/binlist

---

### Post by Chilli Bob on 2007-11-29
Thanks All

---

### Post by viking777 on 2007-11-29
```
dpkg --get-selections
```

---

