---
title: "ndiswrapper"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by haveacigar on 2007-01-20
Hey, im trying to install ndiswrapper to get the internet working, but i am still having some problems.

First of all (i am a complete noob to linux) i was presented with a message that says that an ubuntu cd was detected and i was able to install make with it. Then I closed the window and wasnt able to get the window up again. It just came up with the file system... does anyone know how to get it up again?

Also when trying to get the ndiswrapper to install i got this message

```

alanmonger@alanmonger-desktop:~/Desktop/ndiswrapper-1.33$ sudo make install

make -C driver install
make[1]: Entering directory `/home/alanmonger/Desktop/ndiswrapper-1.33/driver'

Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
 
 KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory 
`/home/alanmonger/Desktop/ndiswrapper-1.33/driver'
make: *** [install] Error 2


```

But i have no idea what this error is, or means.

Any help would be much appreciated

Cheers

Haveacigar

---

### Post by teaker1s on 2007-01-20
have a look at the link in my signature, it's for broadcom chipset, but will explain how to compile ndiswrapper etc:guitar:

---

### Post by euler_fan on 2007-01-20
[Look Here]("http://ubuntuforums.org/showthread.php?t=197102") for a great package. I have used it many times and it works like a charm for my machine.

---

