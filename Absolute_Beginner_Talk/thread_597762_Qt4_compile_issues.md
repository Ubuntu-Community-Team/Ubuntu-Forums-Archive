---
title: "Qt4 compile issues"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ivanristeski on 2007-10-30
Hello everybody, I'm new in kubuntu (1month) and i have some issues with Qt-4.3.2. I have installed it from source, made that PATH in .profile and now i cannot compile even a Hello world. this is what i get with qmake -project, qmake, make:

g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o hello.o hello.cpp
hello.cpp:1:24: error: QApplication: No such file or directory
hello.cpp:2:23: error: QPushButton: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:6: error: ‘QApplication’ was not declared in this scope
hello.cpp:6: error: expected `;' before ‘app’
hello.cpp:7: error: ‘QPushButton’ was not declared in this scope
hello.cpp:7: error: expected `;' before ‘hello’
hello.cpp:8: error: ‘hello’ was not declared in this scope
hello.cpp:10: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:4: warning: unused parameter ‘argc’
hello.cpp:4: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

Can anyone help? Please I have tried many and the result is same.

Cheers.

---

### Post by uygaruzunhasan on 2008-01-23
I also got a problem about the Qt4 compiling
I have a Qt4 project and when I try to compile it I stops.
I also tried a simple "hello world" project but result didn't changed
Here is the result:

[B]uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4 -project
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ make
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o main.o main.cpp
Unable to exec g++.real: No such file or directory
make: *** [main.o] Error 2
uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$[/B]

this is my qmake-qt4 version:
[B]uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ qmake-qt4 -v
QMake version 2.01a
Using Qt version 4.3.2 in /usr/lib[/B]

After the eror reports I installed g++ 3.3 , 3.4 , 4.2 one by one but It didn't worked

Those are my g++ versions:
[B]uygar@uygar-laptop-ubuntu:~/Masaüstü/sss$ g++
g++      g++-3.3  g++-3.4  g++-4.2[/B]

:confused:

Ps: This is my first Ubuntu experiance, I install it (7.10) yesterday and I installed all about Qt4 4.3.2 except python libs because my codes are c++. Before Ubuntu, I used Pardus (maybe you don't know it) and Fedora core6 and they were ok compiling (also XP).

---

