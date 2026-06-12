---
title: "help upgrading to glibc 2.14"
date: 2011-12-30
forum: Any Other OS
---

### Post by bruno9779 on 2011-12-30
Hi, I am running Linux mint 12 amd64 (oneiric) and I need to upgrade my glibc version 2.13 to glibc 2.14

I have tried compiling it, but I have encountered some issues:

```
In file included from ../sysdeps/unix/sysv/linux/syslog.c:10:0:
../misc/syslog.c: In function ‘__vsyslog_chk’:
../misc/syslog.c:144:9: warning: variable ‘prioff’ set but not used [-Wunused-but-set-variable]
../misc/syslog.c:123:1: sorry, unimplemented: inlining failed in call to ‘syslog’: function body not available
../misc/syslog.c:155:9: sorry, unimplemented: called from here
make[2]: *** [/src/gnu/glibc-build/misc/syslog.o] Error 1
make[2]: Leaving directory `/src/gnu/glibc-2.14/misc'
make[1]: *** [misc/subdir_lib] Error 2
make[1]: Leaving directory `/src/gnu/glibc-2.14'
make: *** [all] Error 2

```

Is there an easier way to do this? a .deb or a ppa?

I couldn't find any by googling around.

thanks

---

### Post by Perfect Storm on 2011-12-31
Moved to Other OS/Distro Talk.

---

### Post by bruno9779 on 2011-12-31
Ok, this post [here]("http://www.linuxquestions.org/questions/programming-9/glibc-2-14-compilation-issue-898810/") has clarified my ideas.

Upgrading glibc is beyond my skills and beyond the scope of compiling Goblin Camp.
I may try again in a VM later, I am not gonna risk borking my system for a tiny game.

---

