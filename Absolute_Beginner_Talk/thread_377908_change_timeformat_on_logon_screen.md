---
title: "change timeformat on logon screen"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by crom on 2007-03-06
Hi

First off, I downloaded Dapper a few days ago, and so far I am very impressed.

My problem is quite minor, but still annoys me quite alot. 

The clock on the bottom right of the logonscreen is in 12hrs format, and I'd like it to be 24hrs

The "other clocks" on the system (upper right corner in X are all 24 hrs)

Any easy fix for this?

-crm

---

### Post by Ek0nomik on 2007-03-06
If you edit your login screen file you may be able to change it.  I would take a look at that first.  Try to grab the tar.gz, extract it, and than look at the file with the code in it.  There may be an option you can add or change.

---

### Post by crom on 2007-03-06
Thanks for setting my mind in motion :)

/etc/X11/gdm/gdm.conf 
```
# Always use 24 hour clock no matter what the locale.
Use24Clock=true
```

That did the trick.

---

