---
title: "How to download all images of a website ???"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by anuda on 2006-07-11
Hey..
am a dapper user. Can anyone tell me how can I download all images from a website ?? There are webreapers in Windows..but how to do that here ?

Any help is welcome !

Thanks apriori,
AnudA

---

### Post by fluffington on 2006-07-12
You can do this with WGet. I'm not experienced enough with it to know exactly what I'm doing, but I think the following command might work:
```
wget -r -l inf -A gif,jpg,png http://...
```
You can check out the [manual](http://www.gnu.org/software/wget/manual/) or type *man wget* in the terminal for more info, or you can install the package *gwget* (it's in universe) for [GWGet](http://gnome.org/projects/gwget/), a graphical frontend to WGet.

Also, you may want to check out the [DownThemAll!](http://www.downthemall.net/) extension for Firefox.

---

### Post by aysiu on 2006-07-12
There's a Firefox extension called *DownThemAll*. It's great.

---

