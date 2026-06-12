---
title: "how to modify files as root"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-10
I am currently trying to modify modprobe.d and I need to modify it as root.  How do I do such a thing in ubuntu.  Kubuntu was nice because all you had to do was drag your curser over it and click "open as root"

---

### Post by kpkeerthi on 2007-12-10
In terminal, type
```

gksudo gedit /path/to/file

```

---

### Post by luckykar on 2007-12-10
To make it easy in gnome to edit files as root just install the following

sudo apt-get install nautilus-gksu

Once you have it installed restart the xserver by ( ctrl alt backspace) log back in and right click on the file you want to edit and select open as administrator.

---

### Post by antisocialist on 2007-12-10
type
```
gksudo nautilus
```
in terminal and it will open a nautilus (file browser) window as root, be careful though, the restrictions are there for a reason, so dont change anything until you have information from a trusty source that it is safe to do what you are doing.

the command i gave you will give you a window with you as root, apps you run from it are run as root ( i believe)

or do
```
gksudo gedit /path/to/file.you/want.to.edit
```
again, be careful as restrictions are there for a reason

---

### Post by 3rdalbum on 2007-12-10
> **luckykar said:**
> 
Once you have it installed restart the xserver by ( ctrl alt backspace) log back in and right click on the file you want to edit and select open as administrator.

Logging out and then logging back in again is sufficient, and with much less danger of losing data.

---

### Post by luckykar on 2007-12-10
> **3rdalbum said:**
> Logging out and then logging back in again is sufficient, and with much less danger of losing data.

What do you think ctrl alt backspace does....okay I will tell you , it logs you out and back in again...:)

---

