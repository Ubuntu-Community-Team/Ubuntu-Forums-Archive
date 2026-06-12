---
title: "how do u install progams"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by s0198hb on 2007-06-10
hi all

i ahve just download a program call avi2pmp program from maconsoles forum so i can create pmp file but i dont   know how to install it. this is what is in the directory any ideas

[[IMG]http://img148.imageshack.us/img148/5350/screenshotcq2.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotcq2.png)

---

### Post by Kobalt on 2007-06-10
Your application may be available to install from the repositories. Read this to learn more about [installing/removing softwares]("https://help.ubuntu.com/7.04/add-applications/C/install-file.html") in Ubuntu.

---

### Post by Eric_Jardas on 2007-06-10
Nope, avi2pmp is not available to install from the repositories. Based on this picture you just have to run make. 
Open terminal and run:
```
cd ~/Desktop/avi2*
```

and then just run make:
```
make
```

Of course maybe you will miss some dependencies so you'll have to install them too.

---

### Post by s0198hb on 2007-06-10
i have just type make and all it says 

make: *** No rule to make target `/usr/lib64/qt4/mkspecs/linux-g++-64/qmake.conf', needed by `Makefile'. Stop.

?

---

### Post by Delkster on 2007-06-10
> **s0198hb said:**
> make: *** No rule to make target `/usr/lib64/qt4/mkspecs/linux-g++-64/qmake.conf', needed by `Makefile'. Stop.

In order to compile programs from source code you need some extra stuff installed -- install the "build-essential" package if you haven't already. Also, it appears that the application you're trying to compile uses the Qt4 library for its user interface stuff, so you probably need at least the base Qt4 library and its developer version in order to compile the program. Install them with the following command and try again after that.
```
sudo aptitude install build-essential libqt4-dev
```

It may be that the program also needs other additional libraries. If you still get an error, or particularly if you get a different one, let us know and we can probably figure out which ones you need to install.


Edit: Now that I read the error you got more closely, it may be about something else than missing libraries. Try the above nevertheless -- it doesn't do any harm and the libraries aren't that big so you won't be wasting much disk space even if it doesn't help.

---

### Post by johnnyw on 2007-06-10
sorry If what I say is nonsense.. but: have you tried using synaptic? system->administration->synaptic packet manager

hope it helps :D

---

### Post by Arisna on 2007-06-10
Should have looked at the screenshot.  Sorry, please delete.

---

### Post by johnc4510 on 2007-06-10
Here is link to how to install anything in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

