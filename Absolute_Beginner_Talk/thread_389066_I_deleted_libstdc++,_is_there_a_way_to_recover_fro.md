---
title: "I deleted libstdc++, is there a way to recover from the install CD"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by amaskell on 2007-03-20
I am a muppet!
I tried to install the dynu client but when it failed due to the wrong version of library... I tried to fix by linking with ln.
I got fed up with trying and then deleted all the links, at some point must have deleted a file :( 

Whenever I run command I often get this error:

apt-get: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

this is what my /usr/lib directory looks like for libstdc++*

mythtv@bp6:~$ ls -l /usr/lib/libstdc++*
-rw-r--r-- 1 root root 888612 2006-10-08 19:24 /usr/lib/libstdc++.6.2-2.so.3
lrwxrwxrwx 1 root root     18 2007-02-18 19:52 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root 737960 2006-10-20 16:53 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root     18 2007-02-18 19:52 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.8

Any advice other than reinstall?!??!

---

### Post by steve101101 on 2007-03-20
have you tried using the package manager to install the library??

---

### Post by amaskell on 2007-03-20
Hi Steve,
 yep, if I fire up the package manager it prompts for the su password, then dies without any error displayed on screen - not sure if there is a log somewhere else.

---

