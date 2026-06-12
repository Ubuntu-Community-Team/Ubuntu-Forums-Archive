---
title: "[SOLVED] sudo"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by indiana_crook on 2008-03-29
```
caleb@caleb-desktop:~$ sudo su
Sorry, user caleb is not allowed to execute '/bin/su' as root on caleb-desktop.
caleb@caleb-desktop:~$ 
```

I'm getting this when I try use sudo... What's up?

---

### Post by forrestcupp on 2008-03-29
Is caleb the only account on your computer?  It may be set up so that caleb doesn't have any administrative privileges.  You may need to boot into a different account to be able to do that.

---

### Post by indiana_crook on 2008-03-29
Well, caleb is the accout that I usually use, however while i was trying to get firestarter to start at startup, I lost root privilages as caleb... make sense to anyone???

---

### Post by indiana_crook on 2008-03-29
Nevermind!!  I got it. The sudoers file wasn't written write.  I fixed it.  THANKS THOUGH!!

---

