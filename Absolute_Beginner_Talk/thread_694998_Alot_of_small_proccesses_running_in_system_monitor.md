---
title: "Alot of small proccesses running in system monitor .."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Joor on 2008-02-12
I just had a look in system monitor and then its showing 20 or more xrdb 's - what is it ?
[http://img220.imageshack.us/img220/3041/screenshot1fe7.png](http://img220.imageshack.us/img220/3041/screenshot1fe7.png)

---

### Post by jan quark on 2008-02-12
see here

[http://www.xfree86.org/current/xrdb.1.html](http://www.xfree86.org/current/xrdb.1.html)

but that is rather a lot xrdb

---

### Post by klemens on 2008-02-12
did you try to reboot?

---

### Post by Joor on 2008-02-12
Yeah they are gone now after a reboot.

---

### Post by jan quark on 2008-02-12
pls post if they come back :)

and mark this thread as solved when they do not come back :)

---

### Post by jordanmthomas on 2008-02-12
Those are zombie processes, meaning they are dead and not running, but you can't get rid of them (can't kill zombies, right?)

Zombies can happen when a program calls another (in this case something is calling xrdb) and has failed to use the right system call to kill them off for good.  

You can get rid of zombies by killing their parent process.  Basically, what you have here is a buggy program somewhere.

---

