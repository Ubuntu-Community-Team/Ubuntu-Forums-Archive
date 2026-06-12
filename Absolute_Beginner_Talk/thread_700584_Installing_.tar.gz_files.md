---
title: "Installing .tar.gz files"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by levif on 2008-02-18
I've tried several times to install applications from .tar.gz files, and I always get the same result.  After running the configure script, I run make, and every time I get this:
make: *** No targets specified and no makefile found.  Stop.
What am I doing wrong?

---

### Post by ruy_lopez on 2008-02-18
```
sudo apt-get install build-essential
```

will install 'make' and other necessary packages.

---

### Post by Crooksey on 2008-02-18
```

./configure
make
sudo make install
```

If the make command is working, build essential should be installed.

---

### Post by levif on 2008-02-18
> 
```
sudo apt-get install build-essential
```

will install 'make' and other necessary packages.
I tried that, no luck.

---

### Post by levif on 2008-02-18
Build-Essential is installed, but make still doesn't work.

---

### Post by ruy_lopez on 2008-02-18
Did you redo ./configure?

---

### Post by levif on 2008-02-18
I did, but got the same result.

---

### Post by ruy_lopez on 2008-02-18
What does the output of ./configure say? Does it produce an error? If it does, please reproduce error message here.

---

### Post by dcraven on 2008-02-18
The "make" command will only work if the "./configure" command doesn't fail. The last thing the configure script does is create the various Makefiles needed to build the project. If those don't exist, then the configure script failed.

You need to read the final lines of the configure script run to see what the issue is (probably a missed dependancy), fix it, and **the**, run the make command.

Cheers,
~djc

---

### Post by levif on 2008-02-18
Here's what I get:

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

---

### Post by ruy_lopez on 2008-02-18
try 

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by seventhc on 2008-02-18
What exactly is it that your trying to install??

---

### Post by jargoman on 2008-02-18
it's asking for gtk2. The gnome toolkit. open synaptic package manager and look for a file like this. 

libgtk-2.0

Install the most up to date one then try again.

oops beat me to it

---

### Post by dcraven on 2008-02-18
> **jargoman said:**
> it's asking for gtk2. The gnome toolkit. open synaptic package manager and look for a file like this. 

libgtk-2.0

Install the most up to date one then try again.

oops beat me to it

If it's the configure script failing due to a dependancy, there's a good chance it's actually the *-dev package that you're missing.

~djc

---

### Post by levif on 2008-02-18
It worked! Thanks!

---

### Post by Sinkingships7 on 2008-02-18
nevermind lol

please mark this thread as solved.

---

