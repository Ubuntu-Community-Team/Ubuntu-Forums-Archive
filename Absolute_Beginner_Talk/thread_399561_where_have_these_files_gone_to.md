---
title: "where have these files gone to"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-04-02
Hi
I have been trying to install a brother fax machine on to my network for ages now and i'm not getting anywhere fast!

I downloaded the driver from brother and in the package handler it gives a list of files included eg:
./
usr/
usr/bin/
usr/bin/brprintconfij2
usr/lib/
usr/lib/libbrcompij2.so.1.0.2
usr/local/
usr/local/Brother/
usr/local/Brother/inf/
usr/local/Brother/inf/brFAX1940CNfunc
usr/local/Brother/inf/brFAX1940CNrc
usr/local/Brother/inf/brPrintListij2
usr/local/Brother/inf/brio04aa.bcm
usr/local/Brother/inf/brio04ab.bcm
usr/local/Brother/inf/brio04ac.bcm
usr/local/Brother/inf/brio04ad.bcm
usr/local/Brother/inf/paperinfij2
usr/local/Brother/inf/setupPrintcapij
usr/local/Brother/lpd/
usr/local/Brother/lpd/filterFAX1940CN
usr/local/Brother/lpd/psconvertij2
usr/local/Brother/lpd/rastertobrij2

when i look for these files there is no Brother folder in usr/local ? nor any of the others
whats happening?

---

### Post by zvacet on 2007-04-02
Sorry for asking,but did you install package or just copy it?If it is installed you will find it with 
```
whereis package_name ls
```

---

### Post by mpooley on 2007-04-02
ok ta!
this is what i got :
fax1940cnlr:
ls: /bin/ls /usr/share/man/man1/ls.1.gz

I looked in /usr/share/man/man1 and there were dozens of gz files which appear to be some sort of compressed file?

---

