---
title: "Root previleges"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-07-10
So I have only one Ubuntu account and I have to put this password everytime I wanan isnatll something.I thought that was beeing root!

But then when I wanted to install a new window border thingy : I can't copy the folder with the theme to usr/share/themes and it says I'm not root!


What's with this?

---

### Post by T700 on 2006-07-10
By default, Ubuntu uses a security model that does not create a root account.  When you need to do something that requires root, you preface the command with "sudo" (for non graphical apps) or gksudo or kdesu (for graphical apps in Gnome and KDE).

You can also start up your file manager with this code, entered into a terminal:

```
gksudo nautilus
``` 
and do your copying in a graphical interface.

Paul

---

### Post by Jagot on 2006-07-10
You can read some more about it here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Endow on 2006-07-10
Thanks guys.Very informative :)

---

