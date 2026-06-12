---
title: "Configure problems"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Saithn on 2008-01-22
Hey,

I'm a new Ubuntu user trying to use some tools that need to be build. However, I have problems with the ./configure. I've already read quite some forums for this problem, but I'm still stuck.

I am using ubuntu 7.10

The message I get when trying to configure:

```
~/Study/ADK-0.4$ ./configure
loading cache ./config.cache
checking for c++... (cached) c++
  ) works... nor the C++ compiler (c++
configure: error: installation or configuration problem: C++ compiler cannot create executables.
delodic@Delodic:~/Study/ADK-0.4$ 
```

And the Log generated:

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:531: checking for c++
configure:563: checking whether the C++ compiler (c++
  ) works
configure:579: c++
 -o conftest    conftest.C  1>&5
eval: 1: c++
: not found
configure: failed program was:

#line 574 "configure"
#include "confdefs.h"

int main(){return(0);}
```.

I Assume that my c++ compiler isn't working correctly. Probably missing a package.

 Using google, I found [this]("http://www.linuxquestions.org/questions/linux-software-2/configure-error-installation-or-configuration-problem-c-compiler-cannot-create-e-294172/") topic with someone that has kind of the same problem I think. 

So the packages I have, for each I did a sudo apt-get install

> 
build-essential is already the newest version.
libc6 is already the newest version.
libstdc++6 is already the newest version.
g++ is already the newest version. **g++ set to manual installed.**


If I type

```
echo 'main(){}' >> test.cpp
``` And then ```
g++ -v test.cpp
```

I get:

> ~/Study/ADK-0.4$ g++ -v test.cpp
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
 /usr/lib/gcc/i486-linux-gnu/4.1.3/cc1plus -quiet -v -D_GNU_SOURCE test.cpp -quiet -dumpbase test.cpp -mtune=generic -auxbase test -version -fstack-protector -fstack-protector -o /tmp/cc2zaA20.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.1.3
 /usr/include/c++/4.1.3/i486-linux-gnu
 /usr/include/c++/4.1.3/backward
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.1.3/include
 /usr/include
End of search list.
GNU C++ version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) (i486-linux-gnu)
        compiled by GNU C version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2).
GGC heuristics: --param ggc-min-expand=98 --param ggc-min-heapsize=128256
Compiler executable checksum: 3cc47be363985179cfafdceddd0e8f5d
test.cpp: In function ‘int main()’:
test.cpp:2: error: redefinition of ‘int main()’
test.cpp:1: error: ‘int main()’ previously defined here


Here my results are a bit different than in the other topic. Anyway, there was suggested to do the following:

> 
I'm going to assume that you have the compiler that came with your system in /usr/bin ( if not, install it off of your install cd's). to make sure we pick that one up do this:

```

export CC=/usr/bin/gcc

```
and
```

export CXX=/usr/bin/g++
```

and try to reconfigure your program again.


When I execute these commands, nothing really happens. I assume there is some problem because I tried to build the g++ myself and later (perhaps?) used the upt-get to install the g++.

I hope this is enough information, and that someone can help me :)

---

### Post by mikeyphi on 2008-01-22
You might get more advice from the
 Other Community Discussions/ Development & Programming/Programming Talk Forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Saithn on 2008-01-22
Ok thanks, I'll repost this there then. :)

---

