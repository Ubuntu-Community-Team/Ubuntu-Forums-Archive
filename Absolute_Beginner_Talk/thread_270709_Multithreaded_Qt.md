---
title: "Multithreaded Qt?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by hyper_ch on 2006-10-03
Hiya

How can I iinstall a multithreaded qt on edgy? I need to for installing this software here:
[http://www.smcc.demon.nl/camstream/](http://www.smcc.demon.nl/camstream/)

> 
checking location of Qt library...
checking if Qt is multi-threaded... no
Qt is not multithreaded (or its name is wrong). You MUST have a multithreaded
version of the Qt library installed or CamStream will simply not compil


Or if you could recommend me any other live web-stream-software that works with Logitech cams... that would help also...

---

### Post by kuja on 2006-10-03
I think the library you need is libqt3-mt and possibly libqt3-mt-dev also.

```
sudo apt-get install libqt3-mt
``` and maybe
```
sudo apt-get install libqt3-mt-dev
```

---

### Post by hyper_ch on 2006-10-03
both are installed... same problem...

> 
checking location of Qt library...
checking if Qt is multi-threaded... no
Qt is not multithreaded (or its name is wrong). You MUST have a multithreaded
version of the Qt library installed or CamStream will simply not compile.
hyper@hyper-linux:~/Desktop/camstream-060217$ sudo apt-get install libqt3-mt libqt3-mt-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt3-mt is already the newest version.
libqt3-mt-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyper@hyper-linux:~/Desktop/camstream-060217$             


---

### Post by kuja on 2006-10-03
Wait a minute, come to think of it. Camstream is in Ubuntu's Universe repository. If you really want to compile it by hand, you could do a sudo apt-get build-dep camstream. More practically though, why not just install the camstream package?

---

### Post by hyper_ch on 2006-10-04
Oh, that's right. I was searching the apt cache for webcam and camstream didn't appear there... so I went on the net looking for something :)

Anyway, apt-get install camstream worked like a charm :) thx :)

---

