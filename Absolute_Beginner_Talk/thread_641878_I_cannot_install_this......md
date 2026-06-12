---
title: "I cannot install this....."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-15
I want to install screenlets, and I don't know how.

> 
+ INSTALLATION:
--------------------------------------------------------------------------------
Extract the archive into some directory. Navigate to that directory. 
As root-user run "make install" (Ubuntu users just add a leading "sudo"). 

By entering "make menu" (again as root) you can install .desktop-files for the
screenlets (not all, only the more stable ones). That allows easily adding 
your screenlets through the Applications-menu or the Alt+F2 dialog.

To generate the default (and ugly) pydoc-documentation within the docs-
directory, run "make pydoc".

To generate the doxygen-documentation run "make doxydoc" (you need to install 
doxygen first).

To generate the epydoc-documentation (in docs/epydoc) run "make epydoc" (you
need to install python-epydoc first). NOTE: this is the best one ;)

I have no idea what it is talking about. I moved the tar.gz folder I downloaded to Documents, then extracted it there. I do not really know how to get to the directory, except "ls Documents".

Help please!

---

### Post by Squizz on 2007-12-15
[http://ubuntuforums.org/showthread.php?t=589403](http://ubuntuforums.org/showthread.php?t=589403)

---

### Post by taurus on 2007-12-15
Why don't you just add a repo for it to /etc/apt/sources.list and install it using synaptic?

[http://www.screenlets.org/index.php/FAQ](http://www.screenlets.org/index.php/FAQ)

---

### Post by Tristicus on 2007-12-15
Thanks squizz. Taurus....I am a Linux noob......

---

### Post by quinnten83 on 2007-12-15
> **taurus said:**
> Why don't you just add a repo for it to /etc/apt/sources.list and install it using synaptic?

[http://www.screenlets.org/index.php/FAQ](http://www.screenlets.org/index.php/FAQ)

obviously because he doesn't know how.
otherwise he wouldn't refer to compiling from source as installing ;)

---

