---
title: "Accessing other partitions"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by invinian on 2006-11-14
Hello, I am having a problem accessing files from Ubuntu.  Before I installed it, I moved all the data I wanted to keep (i.e. movies, music, pics) into a separate partition from my Windows XP.  Unfortunately I didn't know any better, and I formatted it NTFS (automatically, with Partition Magic).  Now I can see the files using Ubuntu, but I can't access them.  The music files (which are .mp3), for example, are not recognized as audio threads.
Any ideas?
Another issue I'm having is that when I try and use a sudo function, terminal faile to authenticate me, and I'm the only user set up on the OS.
Any help/input would be greatly appreciated.
Thanks.

:) Figured out the sudo problem, and am working on the partition info with the tutorial from Taurus.  Thx to you both

---

### Post by bernied on 2006-11-14
ntfs file support is fairly new in linux, so access is often restricted. So you might only have read-only access. Having said that, it is strange that you can 'see' the files, meaning you can get a directory listing (right?), but cannot open them - is that what you mean by access? you can't access them even to read or copy them elsewhere?

Some answer may lie in your /etc/fstab file. See if you can have a look at it, and maybe copy and paste it here.

However, not being able to sudo is going to be a big bummer if you want to change these things. You won't be able to change your fstab if you cannot sudo. Can you post the exact message that you get when you try to sudo, including what you typed?

---

### Post by taurus on 2006-11-14
Here you go...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

