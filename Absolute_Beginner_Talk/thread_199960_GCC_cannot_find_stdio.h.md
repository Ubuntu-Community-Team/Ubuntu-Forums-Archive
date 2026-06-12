---
title: "GCC cannot find stdio.h"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by holzschuh on 2006-06-19
Hello:
     I am trying to learn the c programming language, but whenever I try to compile error message saying it cannot find stdio.h.  [http://gcc.gnu.org/ml/gcc-help/2005-06/msg00218.html](http://gcc.gnu.org/ml/gcc-help/2005-06/msg00218.html) says  stdio.h should be in /usr/include/stdio.h, but I checked there and it isnt there.
Thank You
- Ty Holzschuh

---

### Post by BoyOfDestiny on 2006-06-19
[QUOTE=holzschuh]Hello:
     I am trying to learn the c programming language, but whenever I try to compile error message saying it cannot find stdio.h.  [http://gcc.gnu.org/ml/gcc-help/2005-06/msg00218.html](http://gcc.gnu.org/ml/gcc-help/2005-06/msg00218.html) says  stdio.h should be in /usr/include/stdio.h, but I checked there and it isnt there.
Thank You
- Ty Holzschuh[/QUOTE]

Try getting libbinio-dev, it's in universe.

---

### Post by Reb on 2006-06-19
If you haven't already, try installing the metapackage build-essential.

---

### Post by petrocelli on 2007-08-08
I have the same problem!
I have programmed in C for many a year and run with (Mandrake) Linux since 2001.
Thought I would try Ubuntu and kubuntu this week.
Now I have turned green but not with envy!
Tried a simple "Hello World!" to check things out and cannot find stdio.h.
Do not know if this is an Ubuntu or a gcc problem.
Tried loading gcc 4.1.2 source which contains stdio.h with -I to find it.
Did then find it but got a long list of errors in that file.
gcc has changed the macros to functions but I do not know how this works.
Then tried loading libbinio-dev which did not solve the problem.
Did not load build-essentials which seemed to be aimed at package management.
I wonder why more people have not reported this problem?
I expect a Linux OS to be accompanied by a working C compiler.
Is Ubuntu only aimed at 'office' desktops?
Incidentally I ticked the 'sources' box in synaptic without result.
Is there anyone else wandering around in this wilderness?
(Petrocelli builds but never seems to get there because of other priorities!)

---

### Post by sad_iq on 2007-08-08
Try the **build-essential **package....and if it fails try installing **libc6-dev**. It will install the stdio.h in usr/include

---

### Post by bwtranch on 2007-08-08
The following files should be in the standard deb package, but you should make sure:

dpkg-dev
file
gcc
g++
libc6-dev
make
patch
perl

You want these to make your life easier:

autoconf
automake
dh-make
debhelper
devscripts
fakeroot
gnupg
g77

You probably know this but you should have the repositories enabled. Build-essential will have most of these, but I would make sure with apt:) I would check them one by one.
gpc
xutils
lintian
pbuilder

---

### Post by petrocelli on 2007-08-09
Loading libc6-dev was what was required.
Am I unreasonable?
I was disappointed to find an incomplete compiler in a linux/unix distribution.
To my mind this is more important than games if space is limited!
I am trying a Debian based distribution in the hope that files are where they should be.
I have spent many an hour finding where Mandrake have tucked them away!
IS THIS A TOPIC FOR A DIFFERENT FORUM?
In the meantime - Thanks folks!

---

