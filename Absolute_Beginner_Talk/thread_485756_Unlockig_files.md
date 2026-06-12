---
title: "Unlockig files"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by rosco99 on 2007-06-27
I am trying to use konqueror to modify my /etc/ppp/pap-secrets file.
I have been told to use sudo konqueror and browse to the file.
However, when I do sudo konqueror I get
xlib:connection to:"0,0" refused by server
xlib : No protocol specified
Konqueror can not connect to X server :0,0.

Are there any other permissions I need?, and if so how do I do this.

All help appreciated.
Ross

---

### Post by Seisen on 2007-06-27
Use "ksudo" in front of konqueror in the terminal.

---

### Post by Nekiruhs on 2007-06-27
> **Seisen said:**
> Use "ksudo" in front of konqueror in the terminal.Its kdesu.

---

### Post by Seisen on 2007-06-27
Thanks for correcting me, I not a KDE user as you can tell.

---

### Post by rosco99 on 2007-06-27
Thanks for advising me of kdesu. Unfortunately kdesu konqueror still comes up with same comment.
xlib:connection to:"0,0" refused by server
xlib : No protocol specified
Konqueror can not connect to X server :0,0.
I can bring up konqueror as an application but cannot open in a terminal.

---

### Post by Seisen on 2007-06-27
You can use vim or nano and open that file that way so you can modify it.

---

### Post by rosco99 on 2007-06-27
I can not open pap-secrets file with vim, it is locked. How do I unlock it?

---

### Post by Seisen on 2007-06-27
type sudo in front of it.

---

### Post by rosco99 on 2007-06-27
OK that did it. 
I modified pap-secrets with sudo vim.
Does anyone know why konqueror will not open in konsole?
See my first post for response I get when I try.

---

