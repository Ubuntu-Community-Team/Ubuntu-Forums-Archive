---
title: "Help with compiling."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-15
hi my sound was't working so I downloaded the driver from a website and I am trying to compile the source code but I get this error

checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

Now I am guessing the default kernal source for ubuntu is different..But I don't know were I would find it or how I would change it.....Also I try to use "make" command but it says "command not found" What am I doing wrong.

Thanks,Much Aprreciated

---

### Post by digby on 2006-07-15
```
sudo apt-get install linux-headers-`uname -r`
```will get you the headers that you need.

You also need to install the package build-essential if you haven't already.

---

### Post by crystal on 2006-07-15
> Also I try to use "make" command but it says "command not found"
You have to install build-essential
```
sudo aptitude update
sudo aptitude install build-essential
```

I cannot help you with the first error, sorry.

---

### Post by zxcvbnm on 2006-07-15
ok,Thanks alot......But how would I find out which kernal I have?

---

### Post by taurus on 2006-07-15
```

uname -r

```

---

### Post by elettronicha on 2006-07-15
uname -r

---

### Post by zxcvbnm on 2006-07-15
Sorry for the stupid questions new to linux by the way........
I installed the linux headers but when I do ./configure The same error comes up.SO I check in the dir it is looking for and I find the header except they are in folders in that dirctory.

So instead of this: usr/src/linux
It shows like this usr/src/linux/Linux-headers 2.6

---

### Post by zxcvbnm on 2006-07-15
Nevermind I was stupid and installed the wrong kernal header...Sory and thanks for the help,Very appreciated

---

