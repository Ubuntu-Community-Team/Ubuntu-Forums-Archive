---
title: "New hard drive....help!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by blop on 2007-09-08
Hey all,

i have just fitted a new hard drive the drive is detected and has been partioned and formatted with gParted. Also it has been mounted.....but i cant get read/write access to it without being the administrator....nor can i change the permissions because it says im not the owner.

Can anyone tell what i can do to enable full read write access to all users.....this drive is supposed to media for my network.

Many thanks!

---

### Post by cjssmo on 2007-09-08
What the problem is is that root owns the HDD.  What you need to do is go to [http://www.ss64.com/bash/](http://www.ss64.com/bash/) and check out the command chown.

It goes something like this 

sudo chown -c new owner file or for a real world example 

sudo chown -c charlie /home/charlie/hdd1

hope this helps

---

### Post by blop on 2007-09-08
thanks!!

that worked a treat!

---

