---
title: "Error:&quot;file:///home&quot;"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-04-17
Hey guys. '

Im currently running the latest flight of Kubuntu Dapper on ym sony vaio laptop. I get the following error when I open almost anything: "home folder", "storage media", or "users forlders". I also get this when opeing things like my flash drive.

[img]http://img226.imageshack.us/img226/3457/error1qv.jpg[/img]

When setting up kubuntu, I made three partitions. (/) about 6GB, (/home) about 7GB, and a swap partition. Is this correct? All opf these are on a same hard drive as my windows XP installation.

Any ideas what might be going on? I will be more than happy to provide any more information needed. 

Thank you very much for your help.

Paul

---

### Post by macdo on 2006-04-17
I think you should move this to the Dapper forum. Dapper is still under development, and things do break... People over there might be more capable of helping you.

The only thing I can think of that might cause that would be incorrectly set permissions - try ```
ls -l /
```
There should be a line like this (amongst others):
drwxr-xr-x    5 root root  4096 2006-02-05 17:27 [COLOR="blue"]home[/COLOR]
If the drwxr-xr-x (which shows what permissions are set) is not the same, then you've found your problem!

---

