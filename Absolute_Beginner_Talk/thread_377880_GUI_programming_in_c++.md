---
title: "GUI programming in c++"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-03-06
he guys. i am an electrical engineer and want to make some GUI applications in c++ under . i have read alot of tutorial and viewed some books on c++ but none discusses how to make gui applications i mean windows ,pannels etc.
however after a lot of work i came to know QT and GTK+ are two gui libraries for c++.
now i don't know how to use them. can anybody give me a reference to the tutorial discussing this(it should be very quick not boaring). also i am using edubuntu linux and tell me does GTK comes installed in linux or not? if not ,which components of GTK should i need to install?should i use QT or GTK or some other?
please tell me or write commend to install components i need to install for this. do i will need  to give extra flags with g++  to compile gui programms?

thanks

---

### Post by yabbadabbadont on 2007-03-06
I'm not positive, but I believe that GTK+ is a C library, not C++.  Just as a heads up.

---

### Post by u04f061 on 2007-03-06
> **yabbadabbadont said:**
> I'm not positive, but I believe that GTK+ is a C library, not C++.  Just as a heads up.

can u give me some reference to c++ library?

---

### Post by yabbadabbadont on 2007-03-06
> **u04f061 said:**
> can u give me some reference to c++ library?

You already mentioned it.  ;)  QT

---

### Post by IYY on 2007-03-06
You have a few options here, but the two best ones are QT and GTK2. Both are entirely different libraries. Both QT and GTK can be used on any Linux system (and I believe they can be compiled for Windows and Mac OS as well), but QT looks and works better in KDE whereas GTK is better in Gnome. QT tends to be a bit more flexible.

---

### Post by po0f on 2007-03-06
u04f061,

If you want a C++ GUI library, you can choose from Gtkmm, wxWidgets, Qt, FLTK, FoxTK.  There are probably more, these are just off the top of my head.  You can also use C libraries in C++ if you want to, so straight GTK is also available.

---

