---
title: "Compiling an old program"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Den013 on 2006-07-13
Hello All,

Ive recently installed Ubuntu because I need to run an old program to help me with my thesis.

This program, called Content, is written in C and it uses a user interface library called Vibrant (written in C too). The problem is that when trying to compile Vibrant it gives these error messages.

```
cc -c -O -I../include -I/usr/X11R6/include -DWIN_MOTIF ncbibs.c
In file included from ncbibs.c:84:
../include/ncbiwin.h:200:19: error: Xm/Xm.h: No such file or directory
../include/ncbiwin.h:201:24: error: Xm/AtomMgr.h: No such file or directory
../include/ncbiwin.h:202:26: error: Xm/BulletinB.h: No such file or directory
../include/ncbiwin.h:203:25: error: Xm/CascadeB.h: No such file or directory
../include/ncbiwin.h:204:25: error: Xm/DrawingA.h: No such file or directory
../include/ncbiwin.h:205:21: error: Xm/Form.h: No such file or directory
../include/ncbiwin.h:206:22: error: Xm/Label.h: No such file or directory
../include/ncbiwin.h:207:21: error: Xm/List.h: No such file or directory
../include/ncbiwin.h:208:22: error: Xm/MainW.h: No such file or directory
../include/ncbiwin.h:209:26: error: Xm/MenuShell.h: No such file or directory
../include/ncbiwin.h:210:23: error: Xm/PanedW.h: No such file or directory
../include/ncbiwin.h:211:26: error: Xm/Protocols.h: No such file or directory
../include/ncbiwin.h:212:22: error: Xm/PushB.h: No such file or directory
../include/ncbiwin.h:213:26: error: Xm/RowColumn.h: No such file or directory
../include/ncbiwin.h:214:26: error: Xm/ScrollBar.h: No such file or directory
../include/ncbiwin.h:215:26: error: Xm/ScrolledW.h: No such file or directory
../include/ncbiwin.h:216:26: error: Xm/Separator.h: No such file or directory
../include/ncbiwin.h:217:21: error: Xm/Text.h: No such file or directory
../include/ncbiwin.h:218:22: error: Xm/TextF.h: No such file or directory
../include/ncbiwin.h:219:24: error: Xm/ToggleB.h: No such file or directory
make: *** [ncbibs.o] Error 1
```

Im not sure if Vibrant requires Motif as there are instructions on how to compile without Motif, when I do that however compiling the Content programs results in 

```
cc -c  -I ../../vibrant/include -I /usr/X11R6/include -O2 -DWIN_MOTIF -fPIC -DINSTALL  utility.c
utility.c:1077:24: error: Xm/DialogS.h: No such file or directory
utility.c:1078: error: syntax error before ‘Nlm_appContext’
utility.c:1078: warning: data definition has no type or storage class
utility.c: In function ‘myProcessAnyEvent’:
utility.c:1081: error: ‘XEvent’ undeclared (first use in this function)
utility.c:1081: error: (Each undeclared identifier is reported only once
utility.c:1081: error: for each function it appears in.)
utility.c:1081: error: syntax error before ‘event’
utility.c:1082: error: ‘XtIMXEvent’ undeclared (first use in this function)
utility.c:1082: error: ‘XtIMTimer’ undeclared (first use in this function)
utility.c:1083: error: ‘event’ undeclared (first use in this function)
make[2]: *** [utility.o] Error 1
```

Is it possible to install Motif and if I do so that would it replace Gnome or can they coexist?

---

### Post by slimdog360 on 2006-07-13
hmm, Im not to sure but try putting this into a terminal
```
sudo apt-get install build-essential
```

edit:then of course try compiling the program again

---

### Post by Den013 on 2006-07-13
```
sudo apt-get install build-essential
```

leads to

```
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
```

I guess Ill have to switch to another linux distribution.

---

### Post by taurus on 2006-07-13
Why do you have to switch to another Linux distro when the error message has nothing to do with Ubuntu?  You need to install either openmotif or lesstif because you can compile whatever program you have in mind since it looks for Xm headers!!!  ](*,)

---

### Post by Den013 on 2006-07-14
Oh that should work? Ill try that.

Please keep in mind running this old program is the main reason for using Ubuntu

---

