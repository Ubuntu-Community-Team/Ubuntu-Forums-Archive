---
title: "how to compile from source ?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-06
I've found many programs that do not have .deb packages
but they have the source
I have no idea how to compile thouse programs
I read the .doc files - but I still have a no idea what they want me to do

could someone give me a link or pose how to compile **step by step ?**

---

### Post by lamego on 2006-08-06
Firs you need to have a C compiler, install it with:
```
sudo apt-get install build-essential
```
Then you need to read the INSTALL or README that comes with the source.
The usual procedure is:
```
./configure
make
sudo make install
```
or if you want to generate a debian package for the program:
```
sudo apt-get install checkinstall
```
and use
```
sudo checkinstall make install
```
instead of "make install"

---

### Post by zxee on 2006-08-06
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Compiling_Programs_from_Source](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Compiling_Programs_from_Source)

Hope that helps.

---

