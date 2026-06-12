---
title: "I Cant Update"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by gangsterhead3 on 2008-03-29
i just installed ubuntu on my laptop and theres no update thing
you know the orange square?
when i installed it on my pc there was like 400 of them but now, it says that my system is up to date.
the same thing happened when i installed ubuntu on my friends pc

---

### Post by wolfen69 on 2008-03-29
what version of ubuntu?

---

### Post by bumanie on 2008-03-29
I had the same issue. I told a friend who gave the following instructions. He said it was a glibc6 problem. Here's the fix
[http://gb.archive.ubuntu.com/ubuntu/...ntu10_i386.deb](http://gb.archive.ubuntu.com/ubuntu/...ntu10_i386.deb)
download the patch (from link) to desktop, then in terminal
> cd ~/Desktop 
> sudo dpkg -i libc6_2.6.1-1ubuntu10_i386.deb
The little orange square should return.

---

### Post by gangsterhead3 on 2008-03-29
i have 7.10 64-bit


i dont know how, but it just appeared when i was installing some thing using automatix

i dont know how i did i and id like to know how i did it
my friend would like to know how so soes anyone know what was the problem?

my frien has 32 bit

---

