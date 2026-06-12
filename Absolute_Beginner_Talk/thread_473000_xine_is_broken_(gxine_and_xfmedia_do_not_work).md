---
title: "xine is broken (gxine and xfmedia do not work)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by SoloSalsa on 2007-06-13
I use Xubuntu.  I tried opening an .avi with gxine.  The splash screen appeared, but never went away.  I killed it.  Tried again, with same outcome.  I removed it, reinstalled: same.  I 'completely removed' it, reinstalled: same.  I tried xfmedia, same.
Neither xfmedia nor gxine come properly.  gxine displays the splash infinitely, and xfmedia never shoes up.  Both, however, appear in the process list, with no computer utilization.

What can I do?

---

### Post by ironfistchamp on 2007-06-13
Have you tried running them from a terminal to see if there is any output. Perhaps something is failing behind the scenes that could help in fixing this. 

Would be easier if we knew what was breaking :p

Ironfistchamp

---

### Post by SoloSalsa on 2007-06-13
Actually, this time, it killed itself; how weird, because it never did that before.
But xfmedia just never ends, so I kill it.  Trust me, nothing to see about it.
Anyway:```
solomon@solomon-red:~$ sudo aptitude install gxine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  gxine 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/285kB of archives. After unpacking 1331kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  gxine 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Selecting previously deselected package gxine.
(Reading database ... 96148 files and directories currently installed.)
Unpacking gxine (from .../gxine_0.5.11-1ubuntu2_i386.deb) ...
Setting up gxine (0.5.11-1ubuntu2) ...

solomon@solomon-red:~$ gxine
gxine: killed by watchdog bite
Aborted (core dumped)
```

---

### Post by SoloSalsa on 2007-06-13
Oy, I just rebooted, and it works.  And I can not reproduce any problem.  Sorry for unnecessary forum clutter.

---

### Post by ironfistchamp on 2007-06-14
No problem. Glad it works for you now :D

Ironfistchamp

---

