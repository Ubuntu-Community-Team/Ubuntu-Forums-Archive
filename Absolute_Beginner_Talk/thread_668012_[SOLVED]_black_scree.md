---
title: "[SOLVED] black scree"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by mattlaw on 2008-01-14
i am running ubuntu 7.1 or Gutsy on a dell latitude d400.  I seem to be getting a none responsive black screen when i close the lid to my laptop.  I searched around and it seems this is a common problem. however since i am so new to linux and ubuntu i dont understand what the problem is or how to fix it.  could someone help please?

---

### Post by xelapond on 2008-01-14
The problem is very common among Linux laptops.  It is when the computer can go into suspend fine, but has trouble getting out.

I don't know if your laptop has an ATI chipset, but this guide helped my MBP start working.

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

I've not tried this one, but it supposedly fixes the problem on an Nvidia chipset,

[http://ubuntuforums.org/showthread.php?t=579781&page=21](http://ubuntuforums.org/showthread.php?t=579781&page=21)

Hope that helps,

Alex

---

### Post by nikoPSK on 2008-01-14
Possibly messed up xorg?

try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Best,
nikoPSK

---

### Post by mattlaw on 2008-01-15
thanks guys

---

### Post by nikoPSK on 2008-01-15
No problem. 8-) Can you please mark this thread as "SOLVED"
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Best,
nikoPSK

---

