---
title: "For some reason..."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by bnex10 on 2007-12-09
I recently changed my password.
I might have messed up exactly twice when I entered my new password.

It won't accept my new password (and the old password).
I can't do any administrative tasks. (Good thing I had the automatic login enabled)

Anyone know how I can reset my password?
Without the admin password and sudo.

---

### Post by jordanmthomas on 2007-12-09
You can boot into recovery mode and change your password.
When your computer is starting up, go to recovery mode on the GRUB screen.
Once it's done booting, you will have root access.  Then, change your user's password.
```
passwd username
```

---

### Post by finer recliner on 2007-12-09
everything in linux on the command line is case sensitive, could this be your problem?


also try typing your password out into a text editor (open office or gedit) just so you can see that you're typing your password how you expect it be. maybe a key on your keyboard is stuck...

---

### Post by bnex10 on 2007-12-09
I don't think any keys are stuck. I'll check anyway.

I used two non-alphanumeric characters in my new password.
I also used only lowercase letters and a few numbers too.

Is Linux picky on non-alphanumeric characters?

---

### Post by CaptainInsaneO on 2007-12-09
I think you just might have fat-fingered it.

I've done this quite a few times, where I thought I was good and it turns out I entered the password wrong both times.

---

### Post by Dr Small on 2007-12-09
That is usually the case. One time I installed Ubuntu on my sister's machine and forgot what password I had just previously typed in twice, half an hour ago... I had to brute force it with all of the known passwords that I use, to get in :D

But, try jordanmthomas' suggestion, as that is the easy way to change your password.

Dr Small

---

