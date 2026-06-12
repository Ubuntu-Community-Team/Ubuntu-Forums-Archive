---
title: "Do all file operations have to be done on terminal?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Squrdel on 2006-09-19
I am logged in as my username, which has su privilidges, but I can do nothing via the gui of any system app. Do all operations have to be done via the terminal? If not, what have I done wrong or omitted to do?

---

### Post by dmizer on 2006-09-19
what do you mean you can do nothing via gui of any system app?

no, not all operations have to be done via terminal.

---

### Post by tommcd on 2006-09-19
To edit files you can type 'gksudo gedit' (without quotes). This gives you a notepad-like text editor that is easy to use.
Synaptic can be configured via GUI. Other things can too. What are you trying to do?

---

### Post by hotbrainz on 2006-09-19
All file operations within the User folder can be done normally as in windows. you can drag, drop, cut ,paste etc etc. But in the root u cant do anything of that sort in GUI. This is to prevent you from  messing up the sytem files. But if you know what you are doing then use the command:

gksudo nautilus
( if you have gnome desktop)

kdesu konqueror
(if you have kde desktop)

This will allow you to do the operations in root mode in GUI.

But my friend Caution...... you can mess up stuff.

Hope this helps.

---

### Post by Squrdel on 2006-09-19
Thanks, hotbrains, that explains the issue. I'll try your solution and heed your warning! I am quite experienced in Windows stuff but am now determined to adopt Linux.

---

### Post by techstop on 2006-09-19
...and if you absolutely must do work in the gui as super user, then Automatix will add nautilus scripts that will let you right-click on files and do things like "sudo gedit <filename>" or open nautilus as root.

---

### Post by Squrdel on 2006-09-19
OK, I tried gksudo nautilus and this is what I got:

(nautilus:7646): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Whats that about? Is there a Session Manager that I should be using?

---

### Post by hotbrainz on 2006-09-19
It will tell you of a load of other rejections as well.... but did you notice a window popping up?

Well this has your file system with you having the privilege to do as you please.

Am i making sense?
Try it again..

---

### Post by Squrdel on 2006-09-19
Yes I did! Now I get it! Thanks.

---

