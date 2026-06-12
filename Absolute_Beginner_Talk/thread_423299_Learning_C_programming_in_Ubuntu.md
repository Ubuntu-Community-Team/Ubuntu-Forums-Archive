---
title: "Learning C programming in Ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-04-25
I'm new to Ubuntu but have a little bit of programming experience in BASIC, Pascal and Fortran (I'm sure this gives away my age!)  As an intellectual challenge I'd like to learn how  to program in C or one of its related forms.  I have a couple of books on C programming but I can' get gcc to compile their example programs, like ones that just print "Hi there!".  It seems not to be able to find stdio.h and it doesn't like the printf command for some reason.  What can you folks recommend to learn some basic C programming using Ubuntu's bcc compiler?

---

### Post by taurus on 2007-04-25
You need to install the build-essential package first.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by lee292 on 2007-04-25
Thanks.  Going to have to wait for the broadband to get fixed at work.  (They get grumpy when i tie up the phone lines!)

---

