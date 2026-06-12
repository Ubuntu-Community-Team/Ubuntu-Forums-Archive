---
title: "Can one Ubuntu install access another Ubuntu install?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-11-02
I just had a perfect install (rollback) to Feisty and had it almost tweaked to my liking. I was doing some editing to xorg.conf to get my mouse buttons going but I am locked out.

sudo nano /etc/x11/xorg.conf has me lost, I can not see the file so I am assuming I have to rewrite the xorg.conf from scratch.  Anyways nano is very confusing, at least for me. 

So I did a fresh install of Feisty and was hoping I could simply copy the xorg.conf and mount the other volume and edit and save the file but I am running into ownership problems, I own both files.

I can not use Natilus to edit the other Feisty install.


Any ideas as this should be a simple do but seems impossible?


TIA

---

### Post by qamelian on 2007-11-02
It should be /etc/X11/xorg.conf.  The X in X11 must be capitalized.

---

### Post by yogo on 2007-11-02
> **qamelian said:**
> It should be /etc/X11/xorg.conf.  The X in X11 must be capitalized.


Thanks, that did it for me, the little x or should I say BIG X.

---

