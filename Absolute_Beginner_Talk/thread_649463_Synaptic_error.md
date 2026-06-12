---
title: "Synaptic error"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by th1bill on 2007-12-24
The following error was received on starting Synaptic;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then brought the terminal up and typed the command and received the following;

bill@bill-spare:~$ dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I am still new and I am lost.

---

### Post by spiderbatdad on 2007-12-24
> **th1bill said:**
> The following error was received on starting Synaptic;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then brought the terminal up and typed the command and received the following;

bill@bill-spare:~$ dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I am still new and I am lost.

!!! typo  sudo dpkg --configure -a

---

### Post by ~LoKe on 2007-12-24
```
sudo dpkg --configure -a
```
Be careful, if you use improper syntax on other commands you could do some damage.

---

### Post by th1bill on 2007-12-25
> **~LoKe said:**
> ```
sudo dpkg --configure -a
```
Be careful, if you use improper syntax on other commands you could do some damage.

Thank you for your help and your advice, it helped.

---

