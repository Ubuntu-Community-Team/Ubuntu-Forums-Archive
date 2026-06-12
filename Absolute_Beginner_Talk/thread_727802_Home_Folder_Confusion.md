---
title: "Home Folder Confusion"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2008-03-18
Hi

I currently have three partitions on a second hard drive -  /, /home and swap. What I had intended to do was to use my /home partition for storing my home folder but it doesn't do that at the moment. It still uses the home folder under root as default. 

I want to use /media/sdb5/gary as my default home folder instead of /home/gary.

How do i do that and get the Home Folder under the Places menu to direct it there?

Many thanks

gazzadtfan

---

### Post by wblancqu on 2008-03-18
Easiest way would be copying all files in your /home/gary to /media/..., then removing directory /home/gary, and recreating it but use a symbolic link to the /media/... folder.

A little less easy way is to adapt your /etc/fstab file.

Grtz

---

### Post by nick_h on 2008-03-18
> A little less easy way is to adapt your /etc/fstab file.
less easy but also the best way to do it.

It might help the OP to read the [Create a separate home partition in Ubuntu](http://psychocats.net/ubuntu/separatehome) article on the psychocats.net site.

---

