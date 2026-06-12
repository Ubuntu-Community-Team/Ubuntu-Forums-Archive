---
title: "Issues with autoreconf and Fuppes [HELP!]"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by anotheraddict on 2008-03-24
Hey guys, just wondering if anyone could help point me in the right direction here.  I've followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=597650") on getting Fuppes installed, and unfortunately I'm getting stuck rather early on

```

dale@dale-desktop:~/fuppes$ sudo autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy --force
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf: running: /usr/bin/autoconf --force
configure.in:51: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
dale@dale-desktop:~/fuppes$ 

```

As you can see, this seems to be a issue with autoreconf and I don't even know where to begin looking to resolve this issue.

I've tried redoing steps 1 through 4 praying that It was something that I just overlooked, but try as I might, I cannot seem to resolve this.  Any help would be appreciated

also, before someone says it, I did attempt to find some documentation about the "use m4_pattern_allow" statement, but still I couldn't find anything that would lead me into the right direction

---

### Post by kingweee on 2008-04-19
I am having the exact same problem. I assume it has something to do with our autoconf configuration.

> autoconf-wrapper: unrecognized option -vfi
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.in: not using Gettext
autoreconf2.50: running: aclocal --force 
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf2.50: configure.in: tracing
autoreconf2.50: running: libtoolize --copy --force
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf2.50: running: /usr/bin/autoconf --force
configure.in:51: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.


---

### Post by kingweee on 2008-04-19
SOLVED:

> sudo apt-get install gettext

---

