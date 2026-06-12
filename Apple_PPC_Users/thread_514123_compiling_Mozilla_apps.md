---
title: "compiling Mozilla apps"
date: 2007-07-31
forum: Apple PPC Users
---

### Post by ajmctaggart on 2007-07-31
Is it possible to compile Thunderbird or Seamonkey apps on the PPC Linux platform?  Have any of you done it?  Im running into roadblocks all over...


Any suggestions on what tools would really help?

thanks,
ajm

---

### Post by stmiller on 2007-07-31
It's a PITA to compile anything Mozilla on any platform. One suggestion to try is this:

```
~# sudo apt-get build-dep firefox mozilla-thunderbird
```

and that will install all dependencies needed to compile these from source.

---

