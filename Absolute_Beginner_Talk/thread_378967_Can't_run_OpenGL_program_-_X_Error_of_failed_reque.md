---
title: "Can't run OpenGL program - X Error of failed request:  BadWindow"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-03-07
I have installed the glut development libraries on my Ubuntu system. I have installed the following packages:-

```
freeglut3-dev_2.4.0-4_amd64.deb
libgl1-mesa_6.4.1-0ubuntu8_amd64.deb
libgl1-mesa-dev_6.4.1-0ubuntu8_amd64.deb
libgl1-mesa-swrast-dev_6.4.1-0ubuntu8_amd64.deb
libglu1-mesa_6.4.1-0ubuntu8_amd64.deb
libglu1-mesa-dev_6.4.1-0ubuntu8_amd64.deb
mesa-common-dev_6.4.1-0ubuntu8_all.deb
xlibs-dev_7.0.0-0ubuntu45_all.deb
```

Now, I try to compile and run the program I got from here:- [http://nehe.gamedev.net/data/lessons/linux/lesson01.tar.gz](http://nehe.gamedev.net/data/lessons/linux/lesson01.tar.gz)

On executing it, I got the following error.

```
smith@pepsi:~/OpenGL/lesson01$ gcc -lglut lesson1.c
smith@pepsi:~/OpenGL/lesson01$ ./a.out
freeglut (./a.out):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  16
  Current serial number in output stream:  19
```

Please tell me what has gone wrong and how I can correct it and make the code run.

---

### Post by smith.norton on 2007-03-08
help!!!!

---

### Post by aberry5555 on 2007-03-08
are you running open source or proprietary graphics drivers and what graphics card do you have?

---

### Post by smith.norton on 2007-03-08
I have not installed any graphics drivers on my Ubuntu.

Mine is NVidia.

---

