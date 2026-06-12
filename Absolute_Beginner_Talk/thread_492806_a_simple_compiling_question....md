---
title: "a simple compiling question..."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-07-05
When compiling things from source...do the files that are "created" or whatever when you ./configure or make or end up in the original folder? or are they spread out throughout the system. I understand that when you do a "make install" that definitely installs. If possible, could someone explain the basic of compiling: its meaning, its purpose, benefits, downsides..etc... I've done some compiling and I'm hoping that I'm not going to have to chase down some loose and useless files

Thanks guys

(still learning the ropes...but I love my ubuntu-box ;) )

---

### Post by whizbaby on 2007-07-05
Compiling is (mostly) for:
-you need a newer version of a software than the one from the repositories
-you need a software that is not in the repositories at all
-you wrote a software

When doing 'make install' as root, the package will be insatalled system-wide. ./configure and make are doing the actual compiling work, files produced by them stay in the source folder. Need2know more?

---

### Post by isaacj87 on 2007-07-05
Nope, I think that covers it. :)

---

### Post by jcronkhite on 2007-07-05
If someone *did* need to know more, did you have a tutorial link or other resource to share?  I mean, just in case someone needs to know (okay I need to know).  Thanks!

---

### Post by isaacj87 on 2007-07-05
haha...i guess i agree. Is there a newbie tutorial for compiling?

---

### Post by whizbaby on 2007-07-06
Hmm googling compiling howto gave e.g. this
[http://www.la-samhna.de/library/compile/index.html](http://www.la-samhna.de/library/compile/index.html)
but I havent read it and cant say if its very useful...

---

### Post by Raineer on 2007-07-06
> **isaacj87 said:**
> haha...i guess i agree. Is there a newbie tutorial for compiling?

A have a link in my sig to a command-line tutorial I'm building.  There are sections on compiling, installing from script, extracting files, etc.  Feel free to review or bookmark :D  I plan to grow the guide quite a bit.

---

### Post by 3rdalbum on 2007-07-06
./configure and make do not put files all over your system - remember, those commands are run with the same permissions as your ordinary user, so they only write to your home directory (actually, they only write straight to their own folder).

If you want to have it so that your compiled programs can be easily removed without having to manually track down every last file, then install the "checkinstall" package, and instead of the "sudo make install" step you should do "sudo checkinstall". This will create a basic Debian package and install that, so if you want to get rid of the program you just compiled all you have to do is apt-get remove it.

Distributing source code is a necessity for programs on Linux and BSD, as it is the lowest common denominator. For instance, I can take the source code of "lame" and compile it for x86, PowerPC, ARM, m68k, etc; any distribution, any POSIX operating system.  You can't run precompiled programs for one architecture on another architecture, but you can compile the source code on any platform.

---

### Post by andrew.46 on 2007-07-14
Hi,

 Saw your post:

> **isaacj87 said:**
> haha...i guess i agree. Is there a newbie tutorial for compiling?

 There is an excellent page:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

           Andrew

---

