---
title: "Suse Studio build won't boot to graphical mode"
date: 2014-03-13
forum: Any Other OS
---

### Post by Tristan_Williams on 2014-03-13
I built a system using Suse Studio.
It includes Xfce and lightdm.

I downloaded the Virtualbox image and booted it.

It only boots to command line, and when I try to issue 'startxfce4' in issues this error:
```

/usr/bin/startxfce4: Starting X server
/usr/bin/startxfce4: line 132: exec: Xinit: not found

```

What went wrong?

---

### Post by tgalati4 on 2014-03-13
Type *startx* in the command line and what happens?

---

### Post by Danny_Hordiyevych on 2014-03-16
I have the exact same problem, if I type *startx* into it it just says *startx: Command not found*.

---

### Post by tgalati4 on 2014-03-16
*startx* is part of *xinit*.  Do you have it installed?

tgalati4@Mint14-Extensa ~ $ apt-cache policy xinit
xinit:
  Installed: 1.3.2-1
  Candidate: 1.3.2-1
  Version table:
 *** 1.3.2-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

I bet *startxfce4* is a large script that calls either *startx* or *xinit * based on a case statement that the configuration files exist (local vs system configuration) and then bootstrap the graphical environment.  It's possible that SUSE Studio is missing a critical piece when assembling an XFCE4 distro.  It could be a bug or something else is going on.

---

