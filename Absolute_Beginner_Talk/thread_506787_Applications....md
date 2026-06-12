---
title: "Applications..."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-22
The question is..where is the aplications??In synaptic package manager it's clearly shown that gcc is installed but after combing the menus thoroughly I can't find it.I hope Calmwin antivirus has been installed with Ubuntu but where is it?

What application should be used to deal with *.rpm files?And how to configure the start up program list(is there anything like msconfig in WinXP?)

All the icons of the hard drives are on the desktop.Can the be removed?How do I select to create icons for the installed applications?

Thanks in advance....

---

### Post by scxtt on 2007-07-22
ubuntu is a .deb based distro - you can't use .rpm files w/o converting them, w/ alien most likely ...

gcc is used from the CLI - open a terminal to use it - no GUI menu item for gcc

check for clam antivirus in synaptic, doubt it's installed by default - why would it be?

startup programs are configured through the session manager - should be in the menu somewhere ...

yes, desktop items can be removed, gconf will do it ...

there's a menu editor, it can change icons in the menu ...

---

### Post by xpod on 2007-07-22
1
```
whereis appname
```

2
Alien is the package for converting rpm`s to deb(in synaptic)
3
[http://techbycolin.com/?p=129](http://techbycolin.com/?p=129)

---

### Post by Hossie on 2007-07-22
gcc has no Menu entry because its a console application. Open a terminal and type "gcc" or "man gcc".

Why do you need a virus scanner? They are normally for scanning mails on a mail server (for windows viruses). Linux is virus-free.

.rpm files are for Redhat-based Distributions, you can convert them using tools like rpm2targz.

What Window Manager are you using? In Ubuntu / Gnome, the desktop icons can be removed using gconf.

---

