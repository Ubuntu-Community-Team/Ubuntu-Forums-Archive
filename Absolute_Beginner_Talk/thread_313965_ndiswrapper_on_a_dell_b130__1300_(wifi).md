---
title: "ndiswrapper on a dell b130 / 1300 (wifi)"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-12-06
i'm following this guide: [http://ubuntuforums.org/showthread.php?t=286924]("http://ubuntuforums.org/showthread.php?t=286924")

first step: remove old versions.

that's my first problem i tried using ndiswrapper before and i ran into a wall and never got it resolved...](*,) 

so i need to know how to remove the old version.

i guess i should start with that and see if i run into any problems after than, can somebody help me out?

---

### Post by econobeing on 2006-12-06
i tried "sudo make uninstall ndiswrapper", that gave me "make: *** No rule to make target `uninstall'.  Stop."

so i tried "sudo apt-get remove ndiswrapper --purge", that gave me" 
"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper"

---

### Post by econobeing on 2006-12-06
okay, i found another guide and deleted everything it told me to, then i got to step 6 on the first guide "sudo make" and it said:

> travis@travis-laptop:~/programsPatchesEtc/ndiswrapper-1.31$ sudo make
Password:
make -C driver
make[1]: Entering directory `/home/travis/programsPatchesEtc/ndiswrapper-1.31/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/travis/programsPatchesEtc/ndiswrapper-1.31/driver'
make: *** [all] Error 2

---

### Post by econobeing on 2006-12-06
apparently i need the kernel sources or something, so "sudo apt-get install linux-headers-2.6.15-27-386" is the current step. *waits for it to download*

---

### Post by econobeing on 2006-12-06
hmm...i got it somehow...awesome :D

---

### Post by CoolHand on 2006-12-06
Just wondering...is there a reason you had to install it from source instead of just using apt-get to install the package?  There is always great merit in knowing how to build from source but it's not always the best option.  I used the package and had it up and running in about 5 or 10 min.

---

