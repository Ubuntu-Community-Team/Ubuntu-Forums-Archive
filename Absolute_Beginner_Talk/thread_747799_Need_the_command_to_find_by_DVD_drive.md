---
title: "Need the command to find by DVD drive"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-06
Hey, is there a command so I can see where my DVD drive is allegedly showing up? As in where the system is seeing it if it is seeing it at all?

Thanks. I think I'm having a problem with my fstab mtab or something like that. 

BTW should there be a link to a folder in my /dev directory?

Just trying to figure out how to get the DVD to read or show up or something!

---

### Post by murlosad on 2008-04-06
you can use > lshw to see if your system is seeing the drive and where it is in the /dev directory.

once you have that you should be able to add it to the fstab manually if you have to.

---

### Post by SlappyPappy on 2008-04-07
Thank you brah.

A couple of other good ones are:

dmesg

and 

lsmod

I'm back up and running like Marathon Man.   :)

---

