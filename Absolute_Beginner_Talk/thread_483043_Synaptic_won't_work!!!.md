---
title: "Synaptic won't work!!!"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-06-24
Whenever I try to load the program it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open() failed,please report

So I opened up a terminal and typed

dpkg --configure -a

and it said I needed to be a super user???

so I typed

su dpkg --configure -a

and it said

su: unrecognised option `--configure'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd




What should I do?

---

### Post by wolfen69 on 2007-06-24
try-    sudo dpkg --configure -a

---

### Post by nirpius on 2007-06-24
Thanks that worked

It turned out the terminal had got stuck when I was installing a .deb package for something and so that couldn't close or something. Everything's fine now.

Cheers

---

