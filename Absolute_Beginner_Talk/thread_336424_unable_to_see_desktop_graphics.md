---
title: "unable to see desktop graphics"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Peter W Pinchar on 2007-01-11
I installed the 386 alt on a pentium3 550mz 20g machine. All I see is text and I do not know what to do to see the desktop. I look forward to learning commands etc in the future, but need to get started with a visual ....thanks in advance for your help

---

### Post by MontanaMax on 2007-01-11
It sounds like you might have installed the server version of Ubuntu. If so, that's no big deal - you can see if you have a X based desktop package installed and start it up by typing

```
startx
```

if that says "command not found" or something like it, you'll need to install the "x-widows" desktop to get a graphical interface. 

```
sudo apt-get install ubuntu-desktop
```

---

