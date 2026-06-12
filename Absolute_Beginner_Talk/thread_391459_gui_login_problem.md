---
title: "gui login problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by arsha bertie on 2007-03-23
hi,
    the gui screen on my machine keeps coming back after logging in, prompting for the password, but i can login via the text console. can anyone please help me.


thanks

---

### Post by wpshooter on 2007-03-23
Sounds like to me that your password needs to be reset.

Seems like to me that I remember reading on here somewhere that this can be done in recovery mode.  But I don't remember the details.

---

### Post by ashref on 2007-04-22
ur home dir is full, so rmove some data from ur home dir.

---

### Post by ashref on 2007-04-27
ariyavunna panike pokavoo. ninde companiyil vere admins onnumille......poor condition

---

### Post by bff7755a on 2007-04-27
Login in consol and try
```
df -h
```
Maybe '/home' partition if sull.

---

### Post by rillip on 2007-04-27
I had this same exact issue occur to me, and like others have said, it occured when the parition was full.  I was able to login to a recovery console, delete some files, and was able to run again (I had an issue for a while where it kept loading the recovery session at boot but I was finally able to get a new one set to load)

---

### Post by mohd_aslam_a on 2007-12-08
u always type the password  wrong! that is ur problem

---

