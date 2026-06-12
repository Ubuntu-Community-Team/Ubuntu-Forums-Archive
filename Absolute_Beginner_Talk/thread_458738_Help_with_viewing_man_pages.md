---
title: "Help with viewing man pages"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by divisortheory on 2007-05-29
I'm trying to look at the man pages for various parts of my system, and they don't seem to be installed.  I've tried this a couple of ways:

$ man read
No manual entry for read

When I click Help from the KDE menu I get the graphical help index.  I then browse down to the UNIX Manual Pages category, and click (2) System Calls. The result is this:

Index for Section 2: System Calls
   intro      Introduction to system calls

So I click the intro link just out of curiosity, and there is another link on the page to syscalls(2).  I click that link, and I get this:

KDE Man Viewer Error
No man page matching to syscall found.

Check that you have not mistyped the name of the page that you want. Be careful that you must take care about upper case and lower case characters!
If everything looks correct, then perhaps you need to set a better search path for man pages, be it by the environment variable MANPATH or a matching file in the directory /etc .

Any ideas how to set this up?  Thanks

---

### Post by yabbadabbadont on 2007-05-29
Make sure that you have the manpages-dev package installed.

---

### Post by hartz on 2007-05-30
You can get additional man pages, eg section 2 and 3C, by installing manpages-dev
```
sudo apt-get install manpages-dev
```

This will give you the man page for "read" and also "fread", for example.

Note: There is also a section on "shell builtins" in the shell man pages.

---

### Post by mozetti on 2007-05-30
I just found this today: [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

