---
title: "Can't compile Qt4 even &quot;hello World&quot;"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by uygaruzunhasan on 2008-01-23
I have a Qt4 project and when I try to compile it I stops.
I also tried a simple "hello world" project but result didn't changed
Here is the result:

uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4 -project
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ make
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o main.o main.cpp
Unable to exec g++.real: No such file or directory
make: *** [main.o] Error 2
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$

this is my qmake-qt4 version:
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4 -v
QMake version 2.01a
Using Qt version 4.3.2 in /usr/lib

After the eror reports I installed g++ 3.3 , 3.4 , 4.2 one by one but It didn't worked

Those are my g++ versions:
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ g++
g++ g++-3.3 g++-3.4 g++-4.2

:confused:

Ps: This is my first Ubuntu experiance, I install it (7.10) yesterday and I installed all about Qt4 4.3.2 except python libs because my codes are c++. Before Ubuntu, I used Pardus  and Fedora core6  (also XP) and they were ok compiling.

---

### Post by mister_pink on 2008-01-23
Did you remember to install build-essential? For some reason they decided that ubuntu users didnt want it by default! This is a bit of a stab in the dark though, it doesn't look like thats the problem.

---

### Post by uygaruzunhasan on 2008-01-23
Thank you for your help it works. I havn't know I need to install it.
Now I can compile "hello world" and one of my project.
But in my main project there is a problem. I can compile it on XP and Pardus(linux) with same codes but not in ubuntu.

```

private slots:

void normalSize()
{
    imageLabel->adjustSize();
    scaleFactor = 1.0;
}

void formStokResim::fitToWindow()
{
        normalSize();
}
```
[HTML]
libs/formStokResim.h:172: eror: extra qualification 'formStokResim::' on member 'fitToWindow'[/HTML]

At first it seems coding fold but it is not.
How come one OS gives this eror report and one OS doesn't? Have you any idea?

---

