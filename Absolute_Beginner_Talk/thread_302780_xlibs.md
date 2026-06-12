---
title: "xlibs"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-11-19
hello,

To install realplayer I need xlibs, but it isn't installable. Cuold you guide me what I can do?
Thanks,

---

### Post by LLRNR on 2006-11-19
Here's what I get with installing xlibs (I don't know what to say about RealPlayer, I never liked it nor used it):
```
LLRNR@DapperDrake:~$ sudo apt-get install xlibs
Password:
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate
```

So I guess you just might try to install one of the 2 recommended packages, since this message only occurs when a package is obsolete.

HTH,

LLRNR

---

### Post by LLRNR on 2006-11-19
On second thought, sorry, this is what I stumbled into: [http://www.real.com/linux?pcode=rn&am](http://www.real.com/linux?pcode=rn&am). I think you could just try to officially download and install it... Good luck!





*Thread closed - Double post of OP. Only one thread is needed. It's bad ethic to start multiply thread on the same topic* - Artificial Intelligence

---

