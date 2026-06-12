---
title: "[SOLVED] reconfigure xorg problems"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by try2lickurelbo on 2007-08-27
I'm having trouble with the sudo dpkg -reconfigure xserver-xorg command.

I just put a different monitor on my system, and I want to run my system at 1280 x 1024 or 1600x1200.  The previous monitor only went up to 1024x768, so I really want to get this to work.

My /etc/X11/xorg file still has all the information from the old monitor :(.

This is the error message i reciever from the terminal when i run sudo dpkg -reconfigure xserver-xorg:


dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

Anyone know whats up?

---

### Post by try2lickurelbo on 2007-08-27
Problem solved with using sudo dpkg -reconfigure -phigh xserver-xorg!

---

### Post by rickycodie on 2007-08-27
sweet! mark it solved!

---

