---
title: "Help with Gparted please"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-22
Hey, I decided to reinstall Ubuntu due the my stupid error because of Mercury Messenger. I want to create a home partition before doing so. I'm using this guide 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

So I am right now in my live cd, using Gparted.

Am i at the point where I need to resize and I'm suppose to chose the size i want.. the thing is, i have no idea what is the size I need.  

Any idea what size I should chose for my home partition?

It says Minimum size 6182 MiB and Maximum size 113184 MiB

Thanks

---

### Post by mrmonday on 2007-03-22
It depends how many documents you want to have. If you will have lots of pictures/ videos, The bigger the better. What size is your Hard drive? It will help give a better idea for us.

---

### Post by julie_lebou on 2007-03-22
My drive is 120... but all my medias are on my external driver. So i suppose I don't need much, i'm just not sure how much and also, an another question, when I installed Ubuntu for the first time, I chose the option to erase everything and install, now i suppose I will have to chiose an another option right? Witch one?

---

### Post by annda on 2007-03-22
if you have a lot of space on your disk (and it seems so), save 5-10 GB for the root filesystem, maybe 1 GB for swap and use the rest as /home.

remember, you can resize the partitions later if you don't like your original setup.

---

### Post by julie_lebou on 2007-03-22
LOL im lost here.... ok I get that, so in the boxes, what do i put under new size and under free space following?

I always considered myself a geek with windows... but now I feel ridiculus haha

---

### Post by annda on 2007-03-22
> **julie_lebou said:**
> My drive is 120... but all my medias are on my external driver. So i suppose I don't need much, i'm just not sure how much and also, an another question, when I installed Ubuntu for the first time, I chose the option to erase everything and install, now i suppose I will have to chiose an another option right? Witch one?

in that case /home will be used mainly for settings and some temp files. i think as low as 1 GB would be enough. but you can have 5 GB just to be on the safe side. as i said, you can resize later.

and choose manual partitioning. **delete** old partitions, create new ones and assign mount points (/, /swap and /home).

---

### Post by julie_lebou on 2007-03-22
I don't think you understood my question... I don't know where to put those numbers.. i have two boxes:

-New size-

-Free space Following-

So I put 5000 MB where? Witch box?
 Free Space?

---

### Post by julie_lebou on 2007-03-22
ok figured it out hehe

---

