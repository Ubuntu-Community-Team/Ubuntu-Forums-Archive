---
title: "Application keeps exiting itself!"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by dustynus on 2008-05-06
The application
DCpp used to work fine on 7.10 amd64 install on my 2nd gen macbook c2d.

In hardy amd64, it runs fine for a couple minutes, then it just shrinks (as if I've exited it.) I'm not touching the keyboard, and it just closes itself...

Any idea why this may be? 

Thanks

---

### Post by ssam on 2008-05-06
if you are having lots of crashes something is very wrong. either you software is messed up to the point where you probably need to do a reinstall or your hardware is faulty.

see if the command
```

dmesg

```
gives anything useful after one of the crashes.

can you select memcheck from the boot menu, and let that run for a few hours (over night is good).

---

### Post by cyberdork33 on 2008-05-06
also, if you start an application from the commandline, you can often get messages in the terminal when it exits.

---

