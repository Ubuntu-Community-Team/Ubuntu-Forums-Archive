---
title: "Wine won't work"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-01-24
I just compiled wine 0.9.6 from source and did the did a sudo make install. When I try to run winecfg however, I get the error: 
```
/usr/local/bin/wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

```
Wine complains about the same library when I try to run "wine". What can I do to fix this. When I installed wine through apt it works fine. The only reason I'm trying from source is so I can have the most recent version and a possible speed increase.

---

### Post by jasay on 2006-01-24
You can also get the newest wine from the [wine specific repo]("http://www.winehq.com/site/download-deb"):```
#WineHQ
deb http://wine.sourceforge.net/apt/ binary/
```

---

