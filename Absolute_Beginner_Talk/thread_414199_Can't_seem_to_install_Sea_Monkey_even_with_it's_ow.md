---
title: "Can't seem to install Sea Monkey even with it's own installer"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-19
Trying to install Sea Monkey the browser and I can't figure out how to use its installer. Please see snapshot. Thanks.

---

### Post by rocknrolf77 on 2007-04-19
Did you run the installer with sudo? If not you can't write to /usr  Maybe install it somewhere in /home so you can add extensions easily. :)

---

### Post by jacatone on 2007-04-19
Yeah, I guess I could if I understood what your talking about. Man, installing software on this OS is ridiculously complicated. It makes me appreciate Windows even more.

---

### Post by Sef on 2007-04-19
Easy way to install Seamonkey.   System > Administration > Syanptic Package Manager > Search > Type in this: seamonkey > check all the boxes > click apply > follow the directions.


> Man, installing software on this OS is ridiculously complicated. It makes me appreciate Windows even more.


It's not hard to install things.  Just it's new, and there are fustrations when things are new.  

> Yeah, I guess I could if I understood what your talking about.

Read [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by jacatone on 2007-04-20
Says it couldn't find it, even though it's only sitting on the desktop. I remember reading an article in Tux magazine about a program or format called "Autopackage". Said that one of the major stumbling blocks for Linux is installing software. This works just like Windows. You download a program, click on it and just keep clicking Next until it's installed. This whole apt-get, Synaptic, aptitude, etc. ordeal is too complicated.

---

### Post by lolwhites on 2007-05-29
If you've downloaded the installer, try logging in as the administrator first:

1) ALT+F2
2) type *gksudo nautilus*
3) give password when prompted
4) navigate to the folder and you should now be able to install.

---

