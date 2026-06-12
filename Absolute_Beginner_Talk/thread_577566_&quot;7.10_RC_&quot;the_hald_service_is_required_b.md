---
title: "&quot;7.10 RC: &quot;the hald service is required but not running"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by sune_cph on 2007-10-16
Hi,

I have installed the 7.10 RC and everything works very well, except I invariably get:

 "the hald service is required but not running" 

whenever I goto System->Preferences->Removable Drives and Media.

I can fix this by a "$ sudo hald" from a terminal, but this seems a little akward to do everytime.

Anyone?

Thanks!

/Sune

---

### Post by twiceasworn on 2007-10-16
That is a rather strange error.  I would look through the log files to figure out why it is not starting at boot.  Until then you can put the 

```
sudo hald
```

in the /etc/rc.local file and that should make it start on startup.

---

### Post by sune_cph on 2007-10-16
When removing the usplash boot screen I notice a "can't start hardware abstraction layer" error (or words to that effect) during boot, however cat/var/log/dmesg doesn't really enlighten me further on this issue (probably because I'm too ignorant!)

Anyway, the rc.local fix works just fine so I'll stick with that!

Thanks a bunch!

/Sune

---

