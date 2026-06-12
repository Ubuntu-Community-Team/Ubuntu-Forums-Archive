---
title: "Rucursively change permissions on files only???"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-07-04
so i was playing around with chmod -R (you know, tryin to further my knowledge of common and popular cli commands) and accidently made EVERY file on my data drive (luckily it wasnt my root partiition) executable. That sucks when trying to open a video in midnight commander and it thinks its an executable instead of a video. Naturally i tried recursively removing the executable chmod with sudo chmod -R -x /data... wich accomplished its job a little to well... removed the x from folders, making it impossible to navigate anywhere

so my question is... is there a way to accomplish chmod -R -x /data and have it only affect files, not directories

---

### Post by BlackMeTaL on 2007-07-04
[http://www.emcken.dk/weblog/archives/37-chmod-distinguish-between-files-and-directories.html](http://www.emcken.dk/weblog/archives/37-chmod-distinguish-between-files-and-directories.html)

---

### Post by Nythain on 2007-07-04
solved with sudo chmod -R a-x /data followed by sudo chmod -R a+X /data

and that concludes my lesson in retardation today

---

### Post by Nythain on 2007-07-04
> **BlackMeTaL said:**
> [http://www.emcken.dk/weblog/archives/37-chmod-distinguish-between-files-and-directories.html](http://www.emcken.dk/weblog/archives/37-chmod-distinguish-between-files-and-directories.html)
thank you for that link... exactly what i was lookin for... a bit better than my ultimate approach

---

