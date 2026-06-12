---
title: "DECENT C++ IDE for Linux!"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-04-07
Edit: C++ works but no IDEs (apart from simple text editors) work!!!
Am I doing something wrong?
KDev gives this:

cd '/home/mjr/mjr/appdev/c/why_wont_you_work' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/mjr/mjr/appdev/c/why_wont_you_work/debug' && cd '/home/mjr/mjr/appdev/c/why_wont_you_work/debug' && CXXFLAGS="-O0 -g3" "/home/mjr/mjr/appdev/c/why_wont_you_work/configure" --enable-debug=full && cd '/home/mjr/mjr/appdev/c/why_wont_you_work/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal:configure.in:8: warning: macro `AM_PROG_LIBTOOL' not found in library
autoheader
automake
autoconf
configure.in:8: error: possibly undefined macro: AM_PROG_LIBTOOL If this token and others are legitimate, please use m4_pattern_allow. See the Autoconf documentation.
make: *** [all] Error 1
*** Exited with status: 2 ***


---

In my conversion from Windows -> Linux I have yet to find a decent IDE that compares to VC++.
Syntax highlighting and a plethora of compiler options alone do not constitute decent!
I mean something with auto-code formatting, error highlighting and autocorrect & autocomplete like the MS tools.

I've tried Eclipse, which crashes a lot, and KDevelop, which is promising but overly complex and doesn't seem to want to compile "hello world" for me. Any ideas, my computer's getting full of IDE's I don't like!

---

### Post by %hMa@?b&lt;C on 2007-04-07
Anjuita I think that is how it is spelled is pretty good.  But I prefer KDevelop

---

### Post by cypherzero on 2007-04-07
Okay, Anjuta doesn't work either. I'm beinning to think I'm missing something important. But I have all the standard C++ tools, what's wrong!+!

---

### Post by Jussi01 on 2007-04-08
Hei, are you running edgy? if so, uninstall the anjuta in the repos - its broken. go to the anjuta site and install it from there. you want version 1.2.4... i think.
also you could try openldev... it is a simpler one but maybe it is suitable for you. [http://www.openldev.org/](http://www.openldev.org/)

hope this helps.

---

### Post by Hieronymus on 2007-04-08
I use Eclipse with the cdt extension for c++, just search for it with aptitude or the synaptic package manager.

Jeroen

---

### Post by LaurelLynn on 2007-04-08
Dear cypherzero,

IBM´s Eclipse can be downloaded for Ubuntu, I have it too.  It is extremely similar to Visual Studio.  Has excellent tutorials (it also comes with all the same blot and slowness).

It is not just for Java and includes plugins for several languages: Python, Ruby, AND C++.

Laurel Lynn

---

