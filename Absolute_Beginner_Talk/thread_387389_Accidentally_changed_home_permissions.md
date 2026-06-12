---
title: "Accidentally changed /home permissions"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-03-18
I was trying to change the permissions in my /home/user/.wine folder but accidentally ended up applying the changes to my entire /home folder.

This is the command I used:

```
sudo chown -R $user:$user /home/user/.wine
```

So upon restarting I got this message after I logged in:

(see attached image)

My question is how can I change the permissions of my /home folder back to the default? What's the command?

Thanks :)

---

### Post by qpwoeiruty on 2007-03-18
oops

---

### Post by PartisanEntity on 2007-03-18
Okay found the solution, in my bodhi.zazen's first post of this thread solved the problem:
[http://www.ubuntuforums.org/showthread.php?t=331855](http://www.ubuntuforums.org/showthread.php?t=331855)

---

