---
title: "uninstalling single  .deb files with dpkg"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Paul_David on 2007-08-29
How do I uninstall a single .deb file with dpkg? I have tried  typing in  sudo dpkg -r  /home/paul/frostwire-4.13.2.i586.deb, but I got an error message:

dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
paul@paul-desktop:~$ 

I don't know where to begin.

---

### Post by rsambuca on 2007-08-29
If it was installed with a .deb file, you can easily uninstall it with Synaptic Package Manager, since it will show up there.  Just choose "complete removal".

---

### Post by SunnyRabbiera on 2007-08-29
well the command you are probably looking for is
dpkg -r frostwire-4.13.2.i586.deb, as that has worked for me sometimes

and yeh you can remove it with synaptic if you installed the thing, or even apt by typing the command:
apt-ger -r frostwire-4.13.2.i586.deb

---

