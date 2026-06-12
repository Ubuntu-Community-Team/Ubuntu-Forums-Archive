---
title: "[SOLVED] Error after ./configure when installing from source."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-12-13
I am new to linux and expecially new to installing source. I am trying to install pidgin 2.3.1 in Ubuntu 6.06. The file is a source file and it gives me a ./configure error "no c complier found in path". The following is a transcript from the terminal :


> checking build system type... i586-pc-linux-gnu
checking host system type... i586-pc-linux-gnu
checking target system type... i586-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH


What should I install so the dependencies are covered and what is the easiest way to install them (apt, synaptic, etc).

---

### Post by foolsh on 2007-12-13
sudo apt-get install build-essential
see if that helps

---

### Post by Dark_Stang on 2007-12-13
You need a c compiler...
sudo apt-get install gcc

---

### Post by RomeReactor on 2007-12-13
Hi. You need to install the **build-essential** package first:
```
sudo apt-get install build-essential
```

Remember to install the necessary dependencies. Since it's for Pidgin, you can run:
```
sudo apt-get build-dep gaim
```

---

### Post by mister_lister on 2007-12-13
Rome Reactor had the best solution, which covered all the dependencies in his last post, I am doing the make right now as I write this. Quite involved just to install a package, I wil avoid source files in the future (if I can help it). It has been doing the make for a half hour up to this point and still not done.

---

