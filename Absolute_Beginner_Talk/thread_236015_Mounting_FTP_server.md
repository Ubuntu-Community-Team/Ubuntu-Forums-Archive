---
title: "Mounting FTP server"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Pawka on 2006-08-14
Hi, 

How I can mount any FTP server to local folder on my machine? I've heard, that I need some external "mount" module or plug-in ao smonething like this, but maybe someone there knows exactly how do this?

---

### Post by dmizer on 2006-08-14
places > connect to server > enter ftp server information.  shezam folder on desktop.

---

### Post by visik7 on 2006-08-14
lufs can mount ftp in a directory afair.
there isn't any precompiled module for lufs so you need to 
A- compile it by yourself (bad)
B- use module assistant (good)
```

$ sudo apt-get install module-assistant linux-headers-`uname -r`
$ sudo module-assistant

```
select lufs from the list and tell module-assistant to compile it 
iirc it should automatically install it so no need to dpkg -i blablabla.deb
bye

---

