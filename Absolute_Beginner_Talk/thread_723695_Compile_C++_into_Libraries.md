---
title: "Compile C++ into Libraries"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by jgrossm1 on 2008-03-13
Hey all

So just switched to ubuntu 7.04 from vista, and am very happy so far. I've been using the gcc compiler for C/C++ programs to compile into an executable, but I was wondering if there was a way to compile into libraries. Using Vista I had just used Visual Studio and set it to compile library, but I can't find anything online that mentions how to set this for gcc, and I'd really prefer not to have to reboot into windows every time I want to create a new C++ class library. So is this possible?

Thanks in advance

---

### Post by Joeb454 on 2008-03-13
how do you mean library? i.e. ```
mylib.o
``` that kind of thing?

if so do ```
gcc -c myfile.c
```

Also there is the g++ compiler for C++ applications :)

Also don't forget to install build-essential by running ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
```

---

### Post by stevescripts on 2008-03-13
This link should help: [http://taonix.wordpress.com/](http://taonix.wordpress.com/)

Steve

---

