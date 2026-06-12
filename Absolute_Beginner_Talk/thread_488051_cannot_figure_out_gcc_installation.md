---
title: "cannot figure out gcc installation"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by hill0093 on 2007-06-29
2 approaches: 1) I have downloaded gcc-4.3-20070622.tar.bz2 but cannot figure out how to install it on ubuntu 7.04, and 2) I have had the Synaptic Package Manager search (on the web I suppose) for gcc getting a bunch of 4.1.2 packages starting with g like gcj (front end). The latter wants me to select packages, but I have no idea which. How do I install gcc on ubuntu 7.04? Or does there appearance in  Synaptic Package Manager window mean they are already installed?

---

### Post by limbourg31 on 2007-06-29
try a sudo apt-get install gcc, if that doesn't work then:
[INDENT]
sudo apt-get install build essential
cd /<directory where you extracted gcc>
./configure
make
sudo make install
[/INDENT] 

[http://gcc.gnu.org/install/](http://gcc.gnu.org/install/) has the installation in detail

---

### Post by macogw on 2007-06-29
I'm not quite sure how the GNU folks expect anyone to install gcc from a tarball, seeing as you need gcc to compile what's in the tarball.  Once you do "sudo apt-get install build-essential" (as limbourg said), gcc and everything necessary for building other stuff from source will be installed.

---

### Post by hill0093 on 2007-06-29
The sudo apt-get install gcc seemed to work. Not sure what it did but it did download stuff. Some or all was already installed. My simple write "Hello" didn't compile though. Have to giveup for now.

---

### Post by Bluecircle on 2007-06-29
```

sdo apt-get build-essential

```

---

### Post by limbourg31 on 2007-07-01
**sudo**  apt-get **install** build-essential

---

### Post by Bluecircle on 2007-07-01
wow I must have been half asleep when I wrote that...

---

### Post by Malibu Illusion on 2007-07-01
> **hill0093 said:**
> The sudo apt-get install gcc seemed to work. Not sure what it did but it did download stuff. Some or all was already installed. My simple write "Hello" didn't compile though. Have to giveup for now.

As others said before you got GCC independently, it'd have been a better idea to install the build-essential package, which contains everything necessary to compile C programs.

You can then try putting this in a file:

```

#include <stdio.h>
main () {
printf ( "Hello world!\n" );
}
```

You can save that as test.c.  It can then be compiled with:

```
gcc -o test test.c
```

Then executed:

```
./test
```

There, simple compilation. =)

Take care.

---

