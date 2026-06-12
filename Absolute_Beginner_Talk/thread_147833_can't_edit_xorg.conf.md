---
title: "can't edit xorg.conf"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by kc0rtg on 2006-03-20
A few weeks ago i asked for help on the forums on gettting my serial mouse to work.  Several very helpfull people lead me through the process.  But now i am not using the live CD and im on a different computer and i cant get it to work again.  I found the instructions
[http://www.ubuntuforums.org/showthread.php?p=604061#post604061](http://www.ubuntuforums.org/showthread.php?p=604061#post604061) but when i follow these directions it doesnt work.

First I access the terminal by pressing CTRL-ALT-F1.
Then i type this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` But when i press the enter key i get this ```
connot stat '/etc/x11/xorg.conf' : No such file or directory
```

So nothing happens.:-k 

Then, i am still at the terminal so i type ```
(gedit:7462):Gtk-WARNING**: cannot open display:
```

I am wanting to get my mouse working on this computer.  I plan on turning this computer into an HTTP and FTP server so some friends and myself can put some files on the web to share.  Any help is greatly appreciated!

EDIT:Oh, i am using the regular install (not base server) of Ubuntu Version 5.10 for PC.

---

### Post by KansasJoe on 2006-03-20
don't know about ur mouse but the x in X11 is capitalized...linux is case sensitive

---

### Post by kc0rtg on 2006-03-20
Hehe.  Well that sure was easy.  I have been using windows for a while i didnt remember anything about case sensitive.  Thanks alot for the help though!  Im in Kansas too.

---

### Post by KansasJoe on 2006-03-20
no prb...where u at in kansas...i'm in gardner about 25 mins from kc...getting ready for a couple inches of snow supposedly

---

### Post by mr.p on 2006-03-20
Just for your information try using the tab completion it greatly reduces these little errors. :) So for example, "cat /etc/X<tab>/xor<tab>". In this case you would have to know that the X was capitalised.

---

### Post by kc0rtg on 2006-03-21
Tab completion, cool deal, thanks!  And im in Wichita its pretty rainy today.

---

