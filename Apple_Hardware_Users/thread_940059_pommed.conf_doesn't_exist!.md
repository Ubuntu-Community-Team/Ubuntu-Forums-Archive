---
title: "pommed.conf doesn't exist!"
date: 2008-10-06
forum: Apple Hardware Users
---

### Post by dustynus on 2008-10-06
Pommed.conf used to exist, then I manually deleted it, reinstalled pommed, pommed still is controlling my brightness and volume keys, but I can't access /etc/pommed.conf 

It's just not there !

Any ideas what happened to it ?

thanks,

---

### Post by hajk on 2008-10-07
Probably not really "reinstalled"... you should try```

$ sudo dpkg-reconfigure pommed
```and check that /etc/pommed.conf is present again.

---

### Post by dustynus on 2008-10-07
Tried that, didn't put pommed.conf back! Still confused

---

### Post by cyberdork33 on 2008-10-07
I attached the default pommed.conf for mactel machines from the latest version of pommed (v1.21)

---

### Post by hajk on 2008-10-07
> **dustynus said:**
> ...then I manually deleted it, reinstalled pommed...Your problem was caused by "manually" deleting that package. This is in general not a good idea as it messes up package management: there usually is a script run when removing/purging some package, which isn't run when you delete it manually. Deleting (removing or purging) a package should be done through your package manager of choice (Synaptic, apt-get or aptitude). You could try the following:```

$ sudo aptitude purge pommed
```
and then install it once more```

$ sudo aptitude install pommed
```
and now that /etc/pommed.conf file should be there.

The message in all this is: don't mess with the package management system. 

Good luck!

---

### Post by dustynus on 2008-10-07
Ah Thank you very much.

Thanks for the information :) Won't mess it up next time.

Working well now.

:guitar:

---

