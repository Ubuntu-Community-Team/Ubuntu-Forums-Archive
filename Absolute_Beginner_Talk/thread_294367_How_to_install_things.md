---
title: "How to install things?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-11-06
Hello ive got an program that i want to install in the install text file it says cd to it and then make and then make install how to do that? :-k I know how to cd to it but when i run the command make it says make: *** No targets specified and no makefile found. Stop.


and when i try make install it says 

make: *** No rule to make target `install'. Stop.

---

### Post by taurus on 2006-11-06
Did you run "./configure" first before you run the "make" command?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
(Look at Section 4...)

---

### Post by phersotty on 2006-11-06
Check to see if your program is already in the synaptic package manager.  If it is then you can install from there without even using the terminal.  If its not try to follow the instructions that were provided for compiling the program.  Sometimes third-party progams are straight-forward and sometimes they require more advanced knowledge of the filesystem.

---

### Post by GStubbs43 on 2006-11-06
Did you try installing build-essential?
```
sudo aptitude install build-essential
```
then ```
./configure
``` then make and sudo make install (or [checkinstall]("https://wiki.ubuntu.com/CheckInstall"))

See this: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) 
or this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Dinerty on 2006-11-06
Most common way of intalling programs is like previously mentioned.

```
./configure
```

then

```
make
```

then

```
sudo make install
```

you my get errors regarding missing packages, try Synaptic Package Manager and search for these packages, if in doubt always install -dev.

Make sure build-essential is installed to.

---

### Post by Perfect Storm on 2006-11-06
It really depends which tools the dev(s) of the applications gathered the application together. The best way to find out is to read their homepage/notes or the readme.txt which normally comes with the source.

Mostly uses ./configure, make, make install, but other uses jam, scons, python, scripts or needed manually copy to a distination as an example.

---

