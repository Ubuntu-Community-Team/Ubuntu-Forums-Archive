---
title: "opt dir?"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by JulianYorke on 2005-05-27
can anyone tell me what the /opt/ dir is generally used for, just trying to clear some things up for myself as I am quite the newbie

---

### Post by Xian on 2005-05-27
Alot of distros (Arch, SuSE, Slackware) use that directory to install KDE and Gnome in, and then you also will often find Java and some Mozilla paths there as well.

---

### Post by jobezone on 2005-05-29
[QUOTE=Xian]Alot of distros (Arch, SuSE, Slackware) use that directory to install KDE and Gnome in, and then you also will often find Java and some Mozilla paths there as well.[/QUOTE]
 I think /opt/ means optional, where optional software back in the days would probably be installed. Today, most software we use is optional and easily installable (well, in most linux distributions) in the system's correct folders!

Debian (and Ubuntu I guess) recommends that software that is to be installed system-wide, and is not integrated with the packaging system, should be installed in /usr/local .For example, compiled applications. If you go and see inside this directory, it's got it's own hierarchy similar to the one in /, with /bin /games /include /lib /man /sbin /share and /src !

By I think this wouldn't matter much, so it's your choice if you install in /opt , in /usr/local or in your home dir.

---

### Post by Gsibbery on 2005-05-30
The /opt directory is for "optional" software. Slackware and some other distros use it to put KDE or other "extra" programs in. I usually use it when compiling tarballs from the source since I don't want to mess up the package management system.

---

