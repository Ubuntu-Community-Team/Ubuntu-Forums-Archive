---
title: "building gmrun-0.9.2"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-08-09
Hi,

Trying to build gmrum 0.9.2 ... only I get this error when running ./configure

```
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.0.4
                        gobject-2.0 >= 2.0.4
                        gthread-2.0 >= 2.0.4... yes
checking GLIB_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -pthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gtk+-2.0 >= 2.0.5... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.5) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

pkg-config-path needs to be set but not sure with what ? or maybe I have a dep missing 

can anyone help?

MrG

---

### Post by splintercellguy on 2007-08-09
You don't have to build, just install from the repositories:

sudo apt-get install gmrun

---

### Post by MrGreen on 2007-08-09
Got 0.9.1 installed wanted to try out 0.9.2 ;-)

---

### Post by splintercellguy on 2007-08-09
Do sudo apt-get build-dep gmrun to build any dependencies.

---

### Post by gupta_sumesh63 on 2007-08-09
uninstall gmrun. Reinstall it. This time you'll get gmrun-0.9.2
code
> sudo apt-get remove gmrun

code
> sudo apt-get intsall gmrun

---

### Post by MrGreen on 2007-08-09
Wow! thanks man that did the trick.... ;-) would be even more cool is build it into a .deb will do a search for that one

thanks again

MrG

---

### Post by MrGreen on 2007-08-09
```
[ ~ ] > agi gmrun
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  gmrun
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/45.1kB of archives.
After unpacking 176kB of additional disk space will be used.
Selecting previously deselected package gmrun.
(Reading database ... 146933 files and directories currently installed.)
Unpacking gmrun (from .../gmrun_0.9.1-2_i386.deb) ...
Setting up gmrun (0.9.1-2) ...
```

I missed something lol

---

