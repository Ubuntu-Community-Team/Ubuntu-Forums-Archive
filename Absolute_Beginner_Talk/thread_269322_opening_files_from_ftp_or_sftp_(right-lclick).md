---
title: "opening files from ftp or sftp (right-lclick)"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-01
Hello,

If I create an ftp or sftp connection from Places/Connect to Server/ then mount it on my desktop, connect to it with my password, and browse/edit files, I am having a bit of trouble.

If I want to open index.html (For example), I can right-click on it and select which program to edit it with.  If I use gedit, I can edit the file, save it to the remote disk, etc.  However, no other program seems to work via the "right-click" method.

I have tried Quanta Plus, Screem, gVim, Emacs ... if I choose any of those editors, they all open a blank file.  With gedit, it works.  Nothing else does though.  I am hoping to use some other HTML/CSS/PHP editors with my site, but having the darndest time getting them to open remotely.

Any suggestions ?

Damon

---

### Post by sitedesign on 2006-10-01
You may want to try mounting the locations on a permant basis via your fstab file then all programs will see the files as a part of your main system.

Do a quick search on these forums for mounting of SFTP via fstab.

I do a similar thing for my web sites using SSH mounting, which works great.

---

### Post by thornomad on 2006-10-03
> **sitedesign said:**
> You may want to try mounting the locations on a permant basis via your fstab file then all programs will see the files as a part of your main system.

Hey, thanks for that suggestion; I have been looking for how to hook up the fstab configuration to work with SFTP but haven't had any luck.  I posted a new thread with an appropriate title and hope to find some takers. 

Thanks,
Damon

---

### Post by David A Knight on 2006-10-30
Quanta not working I can may be understand.  Screem, definetly strange, works fine for me, as it should as it is using gnome-vfs the same as gedit, gvim and emacs not working is expected.

Any connection added via the connect to server functionality relies on apps supporting gnome-vfs only, maybe KDE apps will handle the uris via KIO-Slaves not sure.

---

