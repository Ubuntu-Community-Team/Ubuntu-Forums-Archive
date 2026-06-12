---
title: "Error installing mplayer"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-07-06
Hi Guys,

I am trying to install the mplayer gui.

When I type the command ./configure --enable-gui --enable-menu

It falls over with the following error :

>Error: X11 support required for GUI compilation
>
>Check "configure.log" if you do not understand why it failed.

The configure.log states :

============ Checking for X11 headers presence ============
Result is: yes (using /usr/include)
##########################################

============ Checking for X11 ============

#include <X11/Xlib.h>
#include <X11/Xutil.h>
int main(void) { (void) XCreateWindow(0,0,0,0,0,0,0,0,0,0,0,0); return 0; }

cc -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer    -o /tmp/mplayer-conf-16819-15901.o /tmp/mplayer-conf-23266-15901.c -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status

ldd /tmp/mplayer-conf-16819-15901.o
ldd: /tmp/mplayer-conf-16819-15901.o: No such file or directory


#include <X11/Xlib.h>
#include <X11/Xutil.h>
int main(void) { (void) XCreateWindow(0,0,0,0,0,0,0,0,0,0,0,0); return 0; }

cc -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer    -o /tmp/mplayer-conf-16819-15901.o /tmp/mplayer-conf-23266-15901.c -L/usr/lib -lXext -lX11 -lnsl -lpthread
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status

ldd /tmp/mplayer-conf-16819-15901.o
ldd: /tmp/mplayer-conf-16819-15901.o: No such file or directory

Result is: no (check if the dev(el) packages are installed)


Can someone tell me what I need to install to get the dev(el) packages as I cannot find them in Synaptic.

Thanks in advance,

Adam.

---

### Post by taurus on 2006-07-06
Is there any reason you want to build mplayer instead of installing it with apt-get or Automatix?

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by mlind on 2006-07-06
I think you should be installing mplayer directly from Ubuntu repositories if
you're not experienced building stuff manually. It's preferred anyway.

You must enable **multiverse** repository.

and choose between
```

p   mplayer-386                                    - The Ultimate Movie Player For Linux 
p   mplayer-586                                    - The Ultimate Movie Player For Linux 
p   mplayer-686                                    - The Ultimate Movie Player For Linux 
p   mplayer-amd64                                  - The Ultimate Movie Player For Linux
p   mplayer-k6                                     - The Ultimate Movie Player For Linux 
p   mplayer-k7                                     - The Ultimate Movie Player For Linux 

```

for amd
```

sudo aptitude update && sudo aptitude install mplayer-k7

```

---

### Post by adam s on 2006-07-06
Thanks guys,

installed with automatix (an excellent tool)


Chears,

Adam.

---

