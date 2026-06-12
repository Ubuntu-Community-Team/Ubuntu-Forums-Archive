---
title: "Having a little trouble installing a program."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by yatesl on 2008-01-13
I'm trying to install [AlephOne]("http://marathon.sourceforge.net/download/linux.php"), and I got a file entitled "AlephOne-20071103-nolibs.tar.bz2".  I extracted this to my desktop, and following the instructions in the readme, typed in to the terminal:

```
liam@liam-laptop:~$ cd Desktop
liam@liam-laptop:~/Desktop$ cd AlephOne-20071103/
$ ./configure
```

Now, it gave the output 

```
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

However, when I type the next part of the installation  ( $ make), I get the output

```
liam@liam-laptop:~/Desktop/AlephOne-20071103$ make
make: *** No targets specified and no makefile found. Stop.
```


I'm new to Linux, as you can probably tell, and I was wondering what I'm doing wrong here?  It's probably a very simple solution...

---

### Post by JoshuaRL on 2008-01-13
I haven't done any compiling yet, (waiting for RAM to come in the mail) but I think that the issue is that you don't have the necessary packages to build it.  Try:

```

sudo apt-get install build-essential

```

And then try the steps above again.  I think that should work.

---

### Post by taurus on 2008-01-13
You need the build-essential package so install it first before you run the ./configure command again.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by yatesl on 2008-01-13
Cheers you two -- Thanks to that little update thingy, I'm seeing the problem now:

```
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
```

Looks like I have to get the SDL thing before I do.  Seeing as though it's almost half 3 in the morning, I think that can wait until tomorrow.

Again, cheers!

---

### Post by taurus on 2008-01-13
Open synaptic and Search for libsdl-dev package.

---

### Post by autocrosser on 2008-01-13
I've been playing [AlephOne]("http://marathon.sourceforge.net/download/linux.php") for several years now--It is the offspring of the Marathon trilogy that was made for Mac in the 90's & Halo is it's distant cousin...

You need all the libsdl-dev listed in Synaptic--that will get you to first base. Try compiling until you get it.

If you like AlephOne--search for EMR--it's a mod of AlephOne done by the Marathon Map Maker Guild.

---

