---
title: "Synaptic Problems"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by hilarion on 2006-08-31
hi guys, i'm pretty new to linux etc, so i'd value some help, cheers.
i've been looking through Synaptic, and found some stuff i liked like FreeOrion and boson, but when i click install and then apply, i cant find them anywhere. this is getting annnoying, because i cant install the stuff with tarballs either.

---

### Post by dannyboy79 on 2006-08-31
usually applications that you add to your box will get put in either /usr/bin or /usr/local/bin. Alternately you can always go to the command line and type in "sudo find / -name nameofapplication" Example would be "sudo find / -name FreeOrion". Things to remember, Upper and lower case matters. What the above command is doing is searching you root directory which is basically the highest you can go in the OS Tree. That's why I don't like Nautilus, they included a search command but you can't only pick one folder within / which isn't much help when you need to search all the folders under /. etc, usr, bin, boot, var, tmp, etc etc. Once you find it you can add it to your menu by going to Alecart Menu Editor and add the command to your pull down menu.

---

### Post by tatimmer on 2006-08-31
I like to use <updatedb> then to search by file/program name use <slocate name*>.  Some programs install an entry in the system Application menus.

---

### Post by TFX360 on 2006-08-31
> **dannyboy79 said:**
> usually applications that you add to your box will get put in either /usr/bin or /usr/local/bin. Alternately you can always go to the command line and type in "sudo find / -name nameofapplication" Example would be "sudo find / -name FreeOrion". Things to remember, Upper and lower case matters. What the above command is doing is searching you root directory which is basically the highest you can go in the OS Tree. That's why I don't like Nautilus, they included a search command but you can't only pick one folder within / which isn't much help when you need to search all the folders under /. etc, usr, bin, boot, var, tmp, etc etc. Once you find it you can add it to your menu by going to Alecart Menu Editor and add the command to your pull down menu.


Very true, easy for me. But is this really for Human Beings? Way buggy... or am I mistaking...

---

### Post by Garyu on 2006-09-18
FreeOrion in the repo???

All I can find is this
[http://www.freeorion.org/index.php/Compile](http://www.freeorion.org/index.php/Compile)
which says I have to compile and that it will take an hour and that I have to install 112megs of libs before I start... 

Installing with apt would be super... But in which repository do I search? Is this something I would have to use Edgy to get?

---

### Post by Garyu on 2006-09-18
As for finding software... try my thread
[http://www.ubuntuforums.org/showthread.php?t=258611](http://www.ubuntuforums.org/showthread.php?t=258611)
maybe it might help you understand where things end up...

You should be able to find games in /usr/games

---

