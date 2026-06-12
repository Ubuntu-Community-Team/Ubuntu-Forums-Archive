---
title: "Generic xorg.conf file"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by yasoumalaka on 2006-10-09
I modified mine and I cant start up in graphical now. I went back with vi and changed everything back to normal and it still doesn't work. Any suggestions?

---

### Post by gn2 on 2006-10-09
Have you tried to reconfigure accepting default settings?

Type this in a Terminal:

sudo dpkg-reconfigure -phigh  xserver-xorg

---

### Post by yasoumalaka on 2006-10-10
Thanks that worked. How the heck do you remember that stuff?](*,)

---

### Post by bulldog on 2006-10-10
> **yasoumalaka said:**
> Thanks that worked. How the heck do you remember that stuff?](*,)

Just copy & paste it into a textfile and store it on your computer.

I do such a thing whenever I come along something interesting.:D

---

### Post by CatKiller on 2006-10-10
> **yasoumalaka said:**
> Thanks that worked. How the heck do you remember that stuff?](*,)

Actually, that one is listed at the top of your xorg.conf :) But bulldog's suggestion of keeping "interesting" instructions in a text file for later use is a good one.

---

