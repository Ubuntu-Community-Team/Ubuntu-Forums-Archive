---
title: "/etc/hosts question"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mannequin on 2007-04-24
Hey all,

I've gotten in to a discussion on a mailing list about the /etc/hosts file. Basically, I want to know why the default hosts file does something like this:

```
127.0.0.1       localhost
127.0.1.1       your-computer-name-here

...

```


Why is localhost and 'your-computer-name-here' on different subnets?

Thanks!
-M.

---

### Post by tomcheng76 on 2007-04-24
i want to know the answer too
they are for loopback /diagnostic
so why dont use the same , for example 127.0.0.1
or computer name use 127.0.0.2
and why different subnet ?

---

### Post by markitect on 2007-04-24
Check out the thread at:

[http://lists.debian.org/debian-boot/2005/06/msg00639.html](http://lists.debian.org/debian-boot/2005/06/msg00639.html):popcorn: 

That should about some it up if you read through that thread.

---

