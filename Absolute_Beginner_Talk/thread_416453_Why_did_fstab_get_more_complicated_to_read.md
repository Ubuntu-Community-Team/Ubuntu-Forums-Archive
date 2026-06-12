---
title: "Why did fstab get more complicated to read?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by belikralj on 2007-04-21
In dapper /etc/fstab entries were fairly easy to understand (well mostly) you would type /dev/hd*# and then where to mount. What are these new names that I see in my fstab file that replace /dev/hd*#, like **UUID=4556-2ADF**  /media/hdc5     vfat    defaults,utf8,umask=007,gid=46 0       1? I just need a little explanation of what it stands for and maybe if somebody knows why they changed the good thing they had going. As I'm writing this post I got the idea that it may be explained in the mount man pages so I'll take a look there in a minute and post back if I find something.

Thanx

---

### Post by belikralj on 2007-04-21
Oh yeah I forgot to say that that was in my Edgy fstab.

---

### Post by bodhi.zazen on 2007-04-21
If you like you can still use the old method.

/dev/hdxy in fstab.

for some info on uuid : [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

One problem has been that if you (re)format a partition the uuid may change and fstab is not automatically updated.

---

