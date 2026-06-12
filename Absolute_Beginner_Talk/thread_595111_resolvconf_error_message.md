---
title: "resolvconf error message"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by resolv_25 on 2007-10-28
I have the same problem as man that sent post:
[http://ubuntuforums.org/showthread.php?t=121411](http://ubuntuforums.org/showthread.php?t=121411)

After some instalation this error is coming up:
```
  resolvconf: error: /etc/resolvconf/run/interface is not a directory 
```

I still have a connection to Internet, but not to network, so I can't even ping another machine.

I tried with
```
resolvconf -u
```
The same error is being reported.

I have a link run in */etc/resolvconf* that lead to */var/run/resolvconf* but resolvconf doesn't exist on that place.
Then I tried to create* /etc/resolvconf/run/interfaces*, also copied there two files enable-interfaces and resolv.conf.

Actually, my nameservers are placed in */etc/ppp/resolv.conf*

So, I don't know how to resolve this resolver problem...

---

### Post by resolv_25 on 2007-10-29
Well, now seems to be ok.
I don't know what have I done, the same message appears, but network is working.
So, this topic might be closed.

---

