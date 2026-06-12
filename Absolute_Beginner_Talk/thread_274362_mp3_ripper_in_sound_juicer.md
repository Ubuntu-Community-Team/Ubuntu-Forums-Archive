---
title: "mp3 ripper in sound juicer"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-09
i am following this explanation here to get the ability to rip mp3's in sound juicer:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

> maranhao@maranhao:~$ sudo su
root@maranhao:/home/maranhao# gstreamer8.0-lame
bash: gstreamer8.0-lame: command not found
root@maranhao:/home/maranhao#


i don't understand why i have this error

---

### Post by cmaranhao on 2006-10-09
bump

---

### Post by Jagot on 2006-10-09
He was installing the package gstreamer8.0-lame, so it would have been:

```
sudo aptitude update
sudo aptitude install gstreamer8.0-lame
```

Having said that, that is a very old guide and that package appears never to have been in the repositories according to packages.ubuntu.com.

Use this guide:

[https://help.ubuntu.com/community/CDRipping?highlight=%28rip%29#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping?highlight=%28rip%29#head-f109ee313aa77bf2997e6499584438e9f7691d58)

---

