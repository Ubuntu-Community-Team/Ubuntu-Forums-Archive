---
title: "Is the command line the same ?"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-08-10
Is the basic command line / terminal the same (apart from sudo I figure) in different distributions of linux, or are there major differences?

---

### Post by heimo on 2005-08-10
There are couple different shells, bash is the usual default. If you know bash, you feel familiar on all Linux command lines - it's very constant - there are more differences in init scripts and package management, but shells are the same - even on other unix systems.

---

### Post by Stormy Eyes on 2005-08-10
[QUOTE=weasel fierce]Is the basic command line / terminal the same (apart from sudo I figure) in different distributions of linux, or are there major differences?[/QUOTE]

The basic commands are essentially the same on all Linuxes. Just about all of them use bash (Bourne Again SHell) by default. FreeBSD uses tcsh, a descendent of the C shell, but even there the basic commands are the same. Commands like ls, mv, cp, tar, less, etc. work the same just about everywhere.

I learned my Unix on an old SunOS machine in college, used FreeBSD, and salvaged clients' data from old SCO servers, so I'd know.

---

### Post by az on 2005-08-10
To split hairs, technically, you are not referring to linux (the kernel) but GNU, the OS which runs on among other kernels, linux.

The GNU toolchain ([http://en.wikipedia.org/wiki/GNU_toolchain](http://en.wikipedia.org/wiki/GNU_toolchain)) is an important part of the GNU OS.

---

### Post by weasel fierce on 2005-08-11
ack, someday I will learn to get the terms right :)

Thanks though. TIme to learn some commands I figure

---

### Post by heimo on 2005-08-11
[QUOTE=weasel fierce]ack, someday I will learn to get the terms right :)

Thanks though. TIme to learn some commands I figure[/QUOTE]
[size=2]
 I just love this... [/size][font=Times New Roman][size=2]Unix Programmer's Manual (1971):
 [/size][/font][font=Times New Roman][size=2][http://cm.bell-labs.com/cm/cs/who/dmr/1stEdman.html]("http://cm.bell-labs.com/cm/cs/who/dmr/1stEdman.html")
It's still usable and covers many basic commands.

But seriously, *man bash *is great (and confusing) place to start your adventure, also lots of tutorials on web. For example:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/]("http://www.tldp.org/LDP/Bash-Beginners-Guide/")

[/size][/font]

---

