---
title: "Depends: libjack0.80.0-0 (&gt;=0.99.0) but it is not installable"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by srafx on 2006-09-30
I'm trying to install mplayer and I finally managed to get it listed to install in Synaptic.  When I try to install it I get:

```
mplayer-386:
 Depends: libjack0.80.0-0 (>=0.99.0) but it is not installable
```

I downloaded the libjack0.80.0-0 and when I try to install that I get:
```
Error: Dependency is not satisfiable: jackd
```

But, I have jackd isntall...need to get mplayer working..let me know if anyone can help.

I did search the forum but all the posts on this didnt really have a solution.  Any help I would appreciate.

---

### Post by xtra2000 on 2006-09-30
Maybe you need to check the version of jackd and update it?  Only a suggestion.

As for me, just run this command: sudo apt-get install mplayer, it works well. 

My system is ubuntu 6.06 LTS dapper.

---

### Post by picpak on 2006-09-30
Try installing libjack0.100.0-0 instead.

---

