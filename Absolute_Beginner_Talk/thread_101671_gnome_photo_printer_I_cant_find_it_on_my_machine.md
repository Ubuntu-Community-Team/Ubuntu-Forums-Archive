---
title: "gnome photo printer I cant find it on my machine"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2005-12-10
Hi , 
I just installed (or so I thought) Gnome Photo Printer using Synaptic. It went thru the motions but I cant find it. I uninstalled and tried again but I still cant find It. Where does it go?

I also downloaded the tar file from frogman site but I get configure errors with that no c compiler in path .
what am i doing wrong ?
jock

---

### Post by ssam on 2005-12-10
not all aplications are good and add them selves to the menu. have a good look through them menus though, it may have a slightly different name. try logging out and back in to see if the menu gets updated.

you could try pressing alt+F2 and typing gnome-photo-printer (if you are lucky it will guess what you are typing.)

you could try installing the package "menu". this is the old fashioned debian menu program, that some programs insert themselves into.

you could file a bug about the package not adding a menu item.

update:
also you can add a new menu item manually by right clicking on the menu, or using smeg

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=jockjunior]Hi , 
I just installed (or so I thought) Gnome Photo Printer using Synaptic. It went thru the motions but I cant find it. I uninstalled and tried again but I still cant find It. Where does it go?

I also downloaded the tar file from frogman site but I get configure errors with that no c compiler in path .
what am i doing wrong ?
jock[/QUOTE]
There are lots of ways to figure out what the program is if it doesn't show up on the menu.  Here is a quick one.  Open a terminal and type:
```

dpkg -L package-name | grep -e /usr/games -e /usr/bin

```
and substitute the name of the package you got with Synaptic or apt-get for "package-name".  You should get back some files from the executables directory.  One of them is likely to be what you need to run in order to start the program.  Once you figure it out, you can create a shortcut or add it to the menu.

---

### Post by ssam on 2005-12-10
the name of the executable (binary) is gnome-photo-printer

---

### Post by jockjunior on 2005-12-10
Hello, sorry for delay in response (grandchildren are here aarrrrrgh!!!!!!!!!!!). tried to hide but they found me.

Thanks to you both for replies will try your suggestions asap

cheers

jock

EDIT  Thanks guys that did it :)

---

