---
title: "How do I remove built-from-source programs?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-06-15
and a second question:

How do I remove incompletely built-from-source programs (compiling failed due to dependency problems)?

---

### Post by loell on 2006-06-15
if the source is in the process of compiling.. then that specific source has not yet installed..

it will only be installed if you do

"make install"

---

### Post by hajk on 2006-06-15
Good question! Always be sure to do the compilation in a non-system directory and to install to the /usr/local tree, in which case removal of the offending software can simply be done by "rm -rf <directory-subtree>". If you want to have another go at compiling that software, commands like "make clean", "make realclean" or 
"make distclean" will get rid of any garbage produced by failed attempts.

BTW, are you sure that you need to compile from source? A search for .deb packages could also be fruitful in many cases...

---

### Post by jrib on 2006-06-15
If you cannot find your program in the repositories and have to build from source, then you should use 'checkinstall' instead of 'make install'.  Checkinstall will create a .deb for you and install it.  That way you can easily remove it using synaptic or some other apt program.

[http://wiki.ubuntu.com/CheckInstall](http://wiki.ubuntu.com/CheckInstall)

---

