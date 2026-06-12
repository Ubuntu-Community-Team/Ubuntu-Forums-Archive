---
title: "Heads up for MBP/Ubuntu 10.10 users"
date: 2010-11-27
forum: Apple Hardware Users
---

### Post by wiznillyp on 2010-11-27
Hello,

I just did a fresh install of 10.10 64-bit on a MacBook Pro 7.1 and after installation and tweaking I discovered that only one core of my dual core CPU was utilized by my OS.  After some research, I figured out the issue and fixed it.

I have since [updated the wiki]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid#CPU") to reflect this change, it is a simple fix.

To see how many cores your OS is using run:
```
cat /proc/cpuinfo | grep 'cpu cores'
```

If that number is not **2** (for you dual core users), hopefully the fix will work.

Cheers.

---

