---
title: "Programming, Compiling C++ .cpp files in Terminal"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Yan1815 on 2007-07-14
Hi, I'm a complete newbie to Ubuntu but i love it, its so great.  I'm currently trying to compile .cpp files from the terminal.  Although many threads talk about g++ i was wondering if anyone could tell me the exact syntax as my experiments have been fruitless thus far.  I have installed build-essential if that helps.  I also tried initially to use anjuta but it didn't seem to produce a file after compilation and i didn't know how to run my program.  When i tried to run it from the **Build** menu, it told me that "The target executable does not exist for this project.".  Any help would be greatly appreciated, thanx.

---

### Post by Diti on 2007-07-14
Hi,

```
g++ your_executable_file -o your_main_file.cpp
```
The *-o* option permit *#include* to work.

---

### Post by jmazzarelli on 2007-07-14
> **Diti said:**
> Hi,

```
g++ your_executable_file -o your_main_file.cpp
```
The *-o* option permit *#include* to work.

I'm pretty sure that should be:
```
g++ source.cpp -o executable_name
```

By the way, if it is a really simple program, Make is smart enough to just do it. If you have a file called program.cpp, just type:
```
make program
```

You don't even need a makefile.

---

### Post by Yan1815 on 2007-07-16
Thanks so much, it really helped to have it explained in very simple terms.  Incidentally, i tested out and jmazzarelli had the correct syntax.  Thanx :-).

---

### Post by bvanpelt on 2007-07-16
The -o option tells the compiler that the next command-line operand is the output file name...

---

### Post by stchman on 2007-07-16
> **Yan1815 said:**
> Hi, I'm a complete newbie to Ubuntu but i love it, its so great.  I'm currently trying to compile .cpp files from the terminal.  Although many threads talk about g++ i was wondering if anyone could tell me the exact syntax as my experiments have been fruitless thus far.  I have installed build-essential if that helps.  I also tried initially to use anjuta but it didn't seem to produce a file after compilation and i didn't know how to run my program.  When i tried to run it from the **Build** menu, it told me that "The target executable does not exist for this project.".  Any help would be greatly appreciated, thanx.

Don't forget to install the build-essential package:

sudo apt-get -y install build-essential

This contains the header files for C/C++.

---

### Post by Majorix on 2007-07-16
What is the difference between
```
sudo apt-get install build-essential
```
and
```
sudo apt-get -y install build-essential
```

Pardon my noobness :D

---

### Post by BlueNoteExpress on 2007-07-16
> **Majorix said:**
> What is the difference between
```
sudo apt-get install build-essential
```
and
```
sudo apt-get -y install build-essential
```

Pardon my noobness :D

The -y automatically answers "Yes" to the questions it asks, usually about how much disk space will be required.  If you leave the '-y' out, you'll just have to manually answer "yes" to the questions.

---

