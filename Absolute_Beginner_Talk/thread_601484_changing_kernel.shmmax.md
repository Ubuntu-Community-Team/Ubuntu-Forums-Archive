---
title: "changing kernel.shmmax"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by redbullmonsta on 2007-11-03
Hi all

I am running Ubuntu 7.10 x86_64

I need to change my kernel.shmmax to at least 64mb

I done this with > root@earth:~# /sbin/sysctl -w kernel.shmmax=67108864
kernel.shmmax = 67108864

...but how do i get this to be remembered for next boot

I used to add this line to my /etc/rc.d/rc.local file (or /etc/init.d/boot.local on suse) they dont seem to exist

(btw i did search the forum but couldn't find anything to help - sorry)

Thanks in advance

Redbullmonsta

---

### Post by redbullmonsta on 2007-11-11
Well i will answer my own post :D

Just add following in /etc/sysctl.conf:

kernel.shmmax = 67108864

Redbullmonsta

---

### Post by matthewcraig on 2007-11-11
Nice one!  Welcome to the community, too.  Would you put [SOLVED] in your subject, so others can learn from your solution?

---

### Post by geoff123 on 2007-12-08
Thanks. I've been trying to figure that out today.

---

