---
title: "Where are icons stored?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-12-23
Hello. I was wondering where the icons for example for VLC player is stored? I would like to know, because I would like to try and make some new ones.

---

### Post by evilc on 2006-12-23
You should find the icons under /user/share/icons

---

### Post by eylisian on 2006-12-23
The above /usr/share/icons is correct. It can be a little daunting to find what you are looking for (I have seen the movie). One way I use to find what I need is to sit in the icon directory and;
```
grep -r <icon-name> .
```
This is better than descending into each dir and having a look, esp. is you have installed a bunch of additional icon packs.

peas.

---

