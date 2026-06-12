---
title: "C Header files not recognized in Ubuntu 5.10"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-10-17
When I try to run a simple C program using header files like stdio.h, stdlib.h, there are compilation errors that the header file is not found.

How do I install and use those header files. Also, I would do BSD socket programming, so I'll need socket.h, inet.h, etc. How do I get them in Ubuntu?

---

### Post by dbd on 2006-10-19
You probably need the build-essential package. Just use the command:
sudo apt-get install build-essential

No idea what you need for BSD socket programming (no idea what it is!). You could try looking around here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

