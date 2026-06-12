---
title: "error - no rule to make target 'install' ?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-02-18
Hi there,

In my efforts to try to get my sm56 modem working, I found a driver with the following instructions for installation:

Login as root 

gunzip sm56-gcc2.tar.gz 

tar -xvf sm56-gcc3.tar 

cd sm56-gcc3 

make install 


Everything seems to work until the last line which gives the following error message:

make: *** No rule to make target 'install'. stop.

What does this mean?

Many thanks!
keno

---

### Post by halfvolle melk on 2007-02-18
Usually, after **cd /the/appropriate/directory** you should do something like this when compiling from source:
```
./configure
./make
./make install
```
In order to do this, you'll also need the **build-essential** package. Also it's likely there's a file called README in /sm56-gcc3 that tells you what needs to be done.

---

