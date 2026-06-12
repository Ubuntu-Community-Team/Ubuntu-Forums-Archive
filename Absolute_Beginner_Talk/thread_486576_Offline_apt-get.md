---
title: "Offline apt-get"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by vlees91 on 2007-06-28
I dont have an internetconnection on my linux-system.
Is it possible to download a package (which I would do with apt-get with linux) to copy it to my linux-system and install it there?

---

### Post by shearn89 on 2007-06-28
Probably - you might be able to find it on sourceforge.net, then download it and copy it across. Then you can just double click the ".deb" package, and it should install fine. It may however be that you have to download the source files, then extract the files to a folder on your linux box, and do "make" "make install" in a terminal... If you're not sure about this, hunt around on the forums - there's definitely a post somewhere on "how to install anything in ubuntu".

---

### Post by scxtt on 2007-06-28
there's an flag for aptitude to just download the .deb file ... oddly enough, it's **download** - as in **aptitude download <package_name>**

---

### Post by vlees91 on 2007-06-28
-.-
i forgot how easy it could be....
[http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx](http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx)
found

---

### Post by vlees91 on 2007-06-28
> **scxtt said:**
> there's an flag for aptitude (maybe apt-get) to just download the .deb file ...

My PC with internet is has WinXP...

---

### Post by scxtt on 2007-06-28
hmm, that changes things :p

you could browse the archives in a web-browser and download .debs --- [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

