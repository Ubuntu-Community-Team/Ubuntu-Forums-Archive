---
title: "BERYL, it just doesnt work"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-12-09
It is starting to make me crazy, i cannot active Beryl and i tried everything.
Every "HOWTO" every driver and even reinstall.

I still getting the error :
"XGL absent, NVIDIA present"   ](*,) 

When i write
```
$ glxinfo | grep direct
```
i get
```
direct rendering: Yes
```
so (i guess) the nvidia driver is installed well (i think)/
(i use kubuntu 6.10 and the video card is Gf4 Ti4200)

please help :cry:
thx ahead

---

### Post by _simon_ on 2006-12-09
That's not an error, it first checks for XGL and if it doesn't find that it then checks for nvidia which you obviously have installed correctly.

What is the actual problem you're having?

Have you tried here: [http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

