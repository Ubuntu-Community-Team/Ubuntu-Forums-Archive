---
title: "Problem Installing Nmap 4.20 on 6.06 LTS"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by cstep on 2007-11-11
Hello to All - A relative new Linux user

If there are two posts from me on this subject I am sorry.  I could not find my first post so I did another one.

I run ./configure nmap-4.20.  The results are all yes except for all of the lines: checking for nmap *.... No.  They are are NO.  The next lines are YES and the last two lines are:

checking build system type...Invalid configuration 'nmap-4.20': machine 'nmap' not reconized.
configure: error:  /bin/sh ./configure nmap-4.20 failed.

A little help to get me on the right track.

Thanks

cstep

---

### Post by cybertoast on 2007-11-11
Ok, here's a really stupid answer (and I'm relatively sure you've tried it already), but just in case: you should be able to install nmap from apt by doing:
```
sudo apt-get install nmap
```

If you're really trying to install from source, make sure you have build-essential installed (sudo apt-get install build-essential). Then go into the nmap src path and ./configure & make & make test & sudo make install.

If neither of these answer your problem, please could you post more details on exactly what you're trying to do.

---

