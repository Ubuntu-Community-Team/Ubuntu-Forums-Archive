---
title: "'make' not working when installing"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by kevin_thome on 2005-10-26
so I'm trying to install alsaplayer from source.

I executed the configure script, then as the wiki says... i put in 'make'

and the terminal spits this message back:

kevin@basement:~/Desktop/alsaplayer-0.99.76$ make
make: *** No targets specified and no makefile found.  Stop.

I have yet to actually manage to install anything from source, if someone could give me a quick how to that'd be great, as I've tried to follow the instructions from [wiki]("https://wiki.ubuntu.com/ConfigureMakeMakeInstall?highlight=%28make%29") but with no luck.

thanks in advance,

-Kevin

---

### Post by Emerzen on 2005-10-26
The make file is created after you run the configure script (./configure).  If that fails or aborts due to errors, no make file will be created.  Read through the output of the ./configure script...often you will notice programs it is looking for or dependencies not met.  If you go back and install them, often through Synaptic, it will work.  Some source programs have an atypical install process, it's always good to look through the folder for any "readme" or "install" text files.  Also, for any successful install from source you will need, at a minimum, the following packages: build-essential and any headers for your kernel.  (Checkinstall is also very useful).

---

### Post by kevin_thome on 2005-10-26
thanks! okay so I kinda got a step further with that...


now I'm getting this error after running the make command


[COLOR="Red"]text.cpp:270: fatal error: opening dependency file .deps/text.Tpo: Permission de nied
compilation terminated.
make[3]: *** [text.lo] Error 1
make[3]: Leaving directory `/home/kevin/Desktop/alsaplayer-0.99.76/interface/tex t'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kevin/Desktop/alsaplayer-0.99.76/interface'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kevin/Desktop/alsaplayer-0.99.76'
make: *** [all] Error 2[/COLOR]

---

### Post by gord on 2005-10-26
you shouldn't really need to do this, but try typing

'sudo make'

---

### Post by Espy on 2005-10-26
Normally, you have to be root only when you run "make install" to install something you've compiled.  It's possible that the plain old "make" will automatically install it, in which case you will, as gord said, need to run it with sudo.

SP

---

### Post by kevin_thome on 2005-10-27
right on! worked like a charm
thanks!

---

