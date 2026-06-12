---
title: "KXDocker Help Needed"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by ariogenki on 2007-02-24
Hey Guys..

I configured my KXDocker fine.

But when I try to make the file. I get the following error at the end.


```
Good - your configure finished. Start make now

root@frank-laptop:/tmp/kxdocker-1.1.4a# make
make  all-recursive
make[1]: Entering directory `/tmp/kxdocker-1.1.4a'
Making all in doc
make[2]: Entering directory `/tmp/kxdocker-1.1.4a/doc'
Making all in .
make[3]: Entering directory `/tmp/kxdocker-1.1.4a/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/tmp/kxdocker-1.1.4a/doc'
Making all in en
make[3]: Entering directory `/tmp/kxdocker-1.1.4a/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/kxdocker-1.1.4a/doc/en'
make[2]: Leaving directory `/tmp/kxdocker-1.1.4a/doc'
Making all in po
make[2]: Entering directory `/tmp/kxdocker-1.1.4a/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/kxdocker-1.1.4a/po'
Making all in src
make[2]: Entering directory `/tmp/kxdocker-1.1.4a/src'
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libKXMouse.la -rpath /usr/lib/kxdocker -avoid-version -module -L/usr/share/qt3/lib -L/usr/lib    -L/usr/lib/ xeplugin_mouse.lo -lXtst libkxdocker.la 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libKXMouse.la] Error 1
make[2]: Leaving directory `/tmp/kxdocker-1.1.4a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/kxdocker-1.1.4a'
make: *** [all] Error 2

```

Help??

---

### Post by ariogenki on 2007-02-24
bump

---

### Post by ariogenki on 2007-02-24
Bump!!!!!!!:ks :ks :ks :ks :ks :ks :ks :ks :ks

---

### Post by ramjet_1953 on 2007-02-25
Do yourself a favour and try KoolDock.
Works fine in GNOME and KDE, even with Beryl!

Much less pain!

Regards,
Roger :cool:

---

### Post by xxzeenoxx on 2007-02-25
> **ramjet_1953 said:**
> Do yourself a favour and try KoolDock.
Works fine in GNOME and KDE, even with Beryl!

Much less pain!

Regards,
Roger :cool:

How did you configure the links for the icons in cooldock?  I installed version 0.3 from the repos, and everytime i go to click on one of my added links, it says it cant find the url...Please help.

---

### Post by ramjet_1953 on 2007-02-26
I assume that you mean that you are trying to add links to websites as items in KoolDock?

If this is the case, I haven't tried this myself. I just use KoolDock to open applications installed on my system.

Anyone tried adding links?

Regards,
Roger :cool:

---

### Post by xxzeenoxx on 2007-02-26
> **ramjet_1953 said:**
> I assume that you mean that you are trying to add links to websites as items in KoolDock?

If this is the case, I haven't tried this myself. I just use KoolDock to open applications installed on my system.

Anyone tried adding links?

Regards,
Roger :cool:

No, i'm dragging the icons for applications on my computer to the dock, but its says, the program name or command cannot be found, please correct the command or URL and try again.

UPDATE:

NM i got it.  I had some dependency issues with some of the KDE libs.  Everything is working fine now...its annoying though that kooldock doesn't pick up all the icons.

---

### Post by tlacuache on 2007-02-28
> **xxzeenoxx said:**
> NM i got it.  I had some dependency issues with some of the KDE libs.  Everything is working fine now...its annoying though that kooldock doesn't pick up all the icons.

What exactly did you do to fix this problem? I've got the same issue.

-SG

---

### Post by xxzeenoxx on 2007-02-28
> **tlacuache said:**
> What exactly did you do to fix this problem? I've got the same issue.

-SG

First, i went to Synaptic Package Manager and Completely Uninstalled kooldock.

Then, i issued the following commands in a terminal:


```
sudo apt-get install build-essential xlibs-dev libqt3-mt-dev
```


```
sudo apt-get install libqt3-compat-headers kdelibs4-dev kdebase-dev
```

Then after this, i went back to Synaptic Package Manager and installed kooldock again...I hope this helps.

---

### Post by ramjet_1953 on 2007-02-28
All I do is right-click on the dock. This opens up a drop-down menu. Put the cursor over Kool Dock and then choose "Edit Quick Launch Menu".

Regards,
Roger :cool:

---

### Post by koshari on 2007-04-30
it would be nice to isolate whick of the kde packages kooldock actually needs for gnome users, 

it would be even nicer if the official package let you know!

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

