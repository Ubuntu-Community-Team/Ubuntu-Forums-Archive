---
title: "cannot launch gtkpod"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by squig on 2007-03-18
```
amy@amy-laptop:~$ sudo apt-get install gtkpod
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mp3gain recode
The following NEW packages will be installed:
  gtkpod
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/492kB of archives.
After unpacking 2036kB of additional disk space will be used.
Selecting previously deselected package gtkpod.
(Reading database ... 88302 files and directories currently installed.)
Unpacking gtkpod (from .../gtkpod_0.99.2-1ubuntu2_i386.deb) ...
Setting up gtkpod (0.99.2-1ubuntu2) ...

amy@amy-laptop:~$ gtkpod
*** glibc detected *** double free or corruption (out): 0x0842ed38 ***
Aborted
amy@amy-laptop:~$

```

I've uninstalled, reinstalled, several times. I can't find any message like this glibc thing on google, that's identical. What is happening here? What should I do? Any help very much appreciated. 

Thanks,
~A

---

### Post by Kobalt on 2007-03-19
I suggest you to open Synaptic and search for gtkpod. It happened sometimes that instead of installing the 'gtkpod' package the command 'sudo apt-get install gtkpod' installed the 'gtkpod-aac' package instead or as well, even though this package is known to be bugy. If you find 'gtkpod-aac' installed on your system then I suggest you try to remove it.

---

### Post by jbayone on 2007-03-19
That's what happened to me.  I had to uninstall gtkpod-aac through Synaptec, then install gtkpod.

---

