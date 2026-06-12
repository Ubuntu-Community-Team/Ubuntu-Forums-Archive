---
title: "Cannot login as root on terminal"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by MrDiaz on 2006-09-23
Hi, for some reason I cannot login as root while using the terminal. All I do is type "su" and then the password as been requested. However, it returns a "su Authentication Failure". Does anyone know what the problem could be?

The password I input is correct, is the same one I use when the system prompts me with the window to log in as root to install or modify something on the system. 

I'm just stuck here. :(

---

### Post by bulldog on 2006-09-23
In Ubuntu we use sudo to get root rights

To use a program with a GUI as root use gksudo

To be root for a longer period of time use sudo -s
You'll be root till you type exit.

You can not login as root as a safety default.

---

### Post by meng on 2006-09-23
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by shashank on 2006-09-23
the short form of sudo is su 
to login tio root type login as ----"root" and password the same u use

---

### Post by MrDiaz on 2006-09-23
excellent, that was helpful. :)

---

