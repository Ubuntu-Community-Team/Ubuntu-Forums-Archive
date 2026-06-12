---
title: "Problem booting Ubuntu"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Mturco11x on 2006-11-04
I burned Ubuntu 6.10 (server) onto a disc and booted from it and I successfully installed it... or so I think.  However, I took the disc out, and booted from the harddrive and it seems to boot but the GUI does not load... when it's done loading it gives me this:

> Ubuntu 6.10 UbuntuServer1 tty1

UbuntuServer1 login:


That's all.  Help please?


Matt

---

### Post by jpeddicord on 2006-11-04
The server edition was made for juust that: servers. It has no GUI by default, because on a server, GUIs waste CPU time and make a server slow. If you want a GUI server, I suggest downloading the Desktop edition and installing all of the server packages. (apache2, mysql, php, etc.)

Jacob

---

### Post by annda on 2006-11-04
or just login and download the desktop packages:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Mturco11x on 2006-11-04
Thank you both.

Firstly, would I get full functionality if I installed desktop and then loaded Apache and all that good stuff?

Secondly, are those two commands all it would take or would I need to do addition steps?


Thanks,
Matt

---

### Post by annda on 2006-11-04
personally, i've done it the other way around: installed desktop first and then added apache/php/mysql & co. but i don't see why you should have to reinstall if you already have the whole server setup. just go ahead and add the desktop - yes, those 2 simple commands are all you need for the gnome desktop. if you prefer KDE or XFCE, substitute 'kubuntu' or 'xubuntu' for 'ubuntu'.

have fun!

---

