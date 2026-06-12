---
title: "what is the c++ app on ubuntu?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-02
what app can be compared to c++ on windows?
is it dc++? thanks

---

### Post by tbrminsanity on 2006-08-02
I use gcc, g++, or c++
In terminal input the following:

gcc -c name.cpp     // compile c++ file to object file
gcc -o name name.o  // create executable
./name              // run executable

Here is a tutorial if you need more info:
[http://www.cs.uregina.ca/Links/class-info/cplusplus/compile-run.html](http://www.cs.uregina.ca/Links/class-info/cplusplus/compile-run.html)

---

### Post by rck_hitokiri on 2006-08-02
thanks bro for the help!

---

### Post by cstudent on 2006-08-02
Install the build-essential package. It will give you the C++ compiler. You'll need the extra included repositories enabled in your sources.list.

```

sudo aptitude install build-essential

```

---

### Post by tospig on 2006-08-02
I use Anjuta as a nice gui editor compilor builder thingy-ma-jig :)

---

### Post by moma on 2006-08-02
Two C++ and STL (Standard Template Library) samples.

o--> [test-std1.cpp]("http://home.online.no/~osmoma//tmp/test-std1.cpp")

o--> [test-std2.cpp]("http://home.online.no/~osmoma//tmp/test-std2.cpp")

c++ reference:
o--> [http://www.cppreference.com/]("http://www.cppreference.com/")

---

